[comment]: # "Auto-generated SOAR connector documentation"
# Tenable\.io

Publisher: Splunk  
Connector Version: 1\.0\.1  
Product Vendor: Tenable  
Product Name: Tenable\.io  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 5\.2\.0  

This app integrates with the Tenable\.io API to provide endpoint\-based investigative actions

[comment]: # " File: README.md"
[comment]: # "  Copyright (c) 2022 Splunk Inc."
[comment]: # "Licensed under the Apache License, Version 2.0 (the 'License');"
[comment]: # "you may not use this file except in compliance with the License."
[comment]: # "You may obtain a copy of the License at"
[comment]: # "    http://www.apache.org/licenses/LICENSE-2.0"
[comment]: # "Unless required by applicable law or agreed to in writing, software distributed under"
[comment]: # "the License is distributed on an 'AS IS' BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,"
[comment]: # "either express or implied. See the License for the specific language governing permissions"
[comment]: # "and limitations under the License."
[comment]: # ""
For more information about Tenable.io Scan Targets, please see their documentation
[here](https://docs.tenable.com/tenableio/Content/Scans/AboutScanTargets.htm)


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Tenable\.io asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**access\_key** |  required  | password | Access Key
**secret\_key** |  required  | password | Secret Key

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[list scans](#action-list-scans) - Retrieve the list of configured scans  
[list scanners](#action-list-scanners) - Retrieve list of scanners that the current user is allowed to use  
[list policies](#action-list-policies) - Retrieve the list of configured polcies  
[scan endpoint](#action-scan-endpoint) - Scans a host using the selected scan policy ID  
[delete scan](#action-delete-scan) - Deletes a scan  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'list scans'
Retrieve the list of configured scans

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**folder\_id** |  optional  | Only return scans within the folder with this ID | numeric |  `tenableio folder id` 
**last\_modified** |  optional  | Only return scans that have been modified since the time specified | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.folder\_id | numeric |  `tenableio folder id` 
action\_result\.parameter\.last\_modified | string | 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.id | numeric |  `tenableio scan id` 
action\_result\.data\.\*\.owner | string | 
action\_result\.data\.\*\.enabled | boolean | 
action\_result\.data\.\*\.creation\_date | numeric | 
action\_result\.data\.\*\.last\_modification\_date | numeric | 
action\_result\.data\.\*\.status | string | 
action\_result\.data\.\*\.shared | boolean | 
action\_result\.data\.\*\.template\_uuid | string | 
action\_result\.data\.\*\.user\_permissions | numeric | 
action\_result\.data\.\*\.read | boolean | 
action\_result\.data\.\*\.type | boolean | 
action\_result\.data\.\*\.uuid | string | 
action\_result\.data\.\*\.legacy | boolean | 
action\_result\.data\.\*\.control | boolean | 
action\_result\.data\.\*\.policy\_id | numeric | 
action\_result\.data\.\*\.permissions | numeric | 
action\_result\.data\.\*\.wizard\_uuid | string | 
action\_result\.data\.\*\.has\_triggers | boolean | 
action\_result\.data\.\*\.schedule\_uuid | string | 
action\_result\.summary\.scan\_count | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list scanners'
Retrieve list of scanners that the current user is allowed to use

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.id | string |  `tenableio scanner id` 
action\_result\.data\.\*\.type | string | 
action\_result\.data\.\*\.linked | boolean | 
action\_result\.data\.\*\.status | string | 
action\_result\.data\.\*\.network\_name | string | 
action\_result\.summary\.scanner\_count | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list policies'
Retrieve the list of configured polcies

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.id | numeric |  `tenableio policy id` 
action\_result\.data\.\*\.creation\_date | numeric | 
action\_result\.data\.\*\.last\_modification\_date | numeric | 
action\_result\.data\.\*\.owner | string | 
action\_result\.data\.\*\.shared | numeric | 
action\_result\.data\.\*\.owner\_id | numeric | 
action\_result\.data\.\*\.no\_target | boolean | 
action\_result\.data\.\*\.visibility | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.template\_uuid | string | 
action\_result\.summary\.policy\_count | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'scan endpoint'
Scans a host using the selected scan policy ID

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**target\_to\_scan** |  required  | Target to scan | string |  `ip`  `host name` 
**policy\_id** |  required  | ID of the scan policy to use | string |  `tenableio policy id` 
**scan\_name** |  optional  | The name of the scan to create | string | 
**scanner\_id** |  optional  | The scanner or scanner group uuid or name | string |  `tenableio scanner id` 
**scan\_timeout** |  optional  | The time \(in seconds\) to wait for a scan to complete | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.target\_to\_scan | string |  `ip`  `host name` 
action\_result\.parameter\.policy\_id | string |  `tenableio policy id` 
action\_result\.parameter\.scan\_name | string | 
action\_result\.parameter\.scanner\_id | string |  `tenableio scanner id` 
action\_result\.parameter\.scan\_timeout | numeric | 
action\_result\.data\.\*\.hostname | string |  `ip`  `host name` 
action\_result\.data\.\*\.score | numeric | 
action\_result\.data\.\*\.low | numeric | 
action\_result\.data\.\*\.medium | numeric | 
action\_result\.data\.\*\.high | numeric | 
action\_result\.data\.\*\.critical | numeric | 
action\_result\.data\.\*\.host\_id | numeric | 
action\_result\.data\.\*\.host\_index | numeric | 
action\_result\.data\.\*\.info | numeric | 
action\_result\.data\.\*\.numchecksconsidered | numeric | 
action\_result\.data\.\*\.progress | string | 
action\_result\.data\.\*\.scanprogresscurrent | numeric | 
action\_result\.data\.\*\.scanprogresstotal | numeric | 
action\_result\.data\.\*\.severity | numeric | 
action\_result\.data\.\*\.severitycount\.item\.\*\.count | numeric | 
action\_result\.data\.\*\.severitycount\.item\.\*\.severitylevel | numeric | 
action\_result\.data\.\*\.totalchecksconsidered | numeric | 
action\_result\.summary\.total\_vulns | numeric | 
action\_result\.summary\.scan\_id | numeric |  `tenableio scan id` 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete scan'
Deletes a scan

Type: **investigate**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**scan\_id** |  required  | The unique identifier for the scan | numeric |  `tenableio scan id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.scan\_id | numeric |  `tenableio scan id` 
action\_result\.data\.\*\.scan\_id | numeric |  `tenableio scan id` 
action\_result\.data\.\*\.delete\_status | boolean | 
action\_result\.summary\.delete\_status | boolean | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 