# Starting a test run and setting up the event system

![events2](https://www.plantuml.com/plantuml/png/ZPJTRk8m48Nl_HIZNYM8xWCWX4f3q2AnRO1eUxboaw5OE7RMdb1u-vNpLuUokxsT-Sx9Z6So3vQueQgGx21oXBtMzAhFZ6Ua3U2Pq2WkVvbAAJJ0BSHRLd938XCbLmHtIyCBVDVc66b5Hak9vivnosZ8BN3FAqafMffRYyMhl3nMGkOjlaZdZqF1KwN406zggEcdT7vLXWCJezyCMhl5KXjgqJJPmdIwSlcri8I8PZQ3p-BuZ5b5GYlN1vwf4STNNMmgh8HwYq-e6hkkeasy7f8rud2iy_5cK8LoLTmGDEpF6vcaAieccrnLlnD5AV55c-EAi5W8MtBA3crTkvVLOeXtO9r-MS5q6kcYr5PGxp6RCSRYBTpFO1cDHZ21o20d37WxYeJJOIponE1UdCSMYOHwio6mPUH4RfYUh8sweVdHxWCmWRNckNiR6uGU36s6SKcmhLHDZ45foBYKhpmxIj-a8uAza8GcP2WjUhftGOTUULCupzm2zCouCsfAgjcczkzSvH9Dq94TaYRRqQX_hKD3XGnLxhTLVp4Wj5Is6slQZUs_o3CI9qxOR7gj6gZdzgAoGBQhz0LPLrGQHu7KFCVclSUTnT-qQUmlW1-62UoG0i-WcTAp-i65IWy6UTxp7w7FU-hxToDBkE5IekmDki3NvC_jnnAjFopShp20LNwZdxmt3bcE_vp3pbrEDygiEHdZL9ThF7qK-T_NtSHhloAb2K6VqBZ417ObPc8lCY0DN45z1e0k9R9Dl7RoUEDjM-WtSpsRBXKddg9Vdz_kJ7sh_QtFTZrwtkuH-p1TzHkoEdq_StTb0ir9HVQ0AgyA-GS0 "events2")

## Classes involved with the ITestListener interface and the Event class

In the startup of a run, 10 classes are directly involved, as shown in the sequence diagram above plus the Event class itself.

The classes may or may not know about the ITestListener interface and the Event class, which handles the standard NUnit events.

|Class|ITestListener|Event|Comment|How to add event listeners|
|---|---|---|---|
|FrameworkController|No|No|The controller of the test run|NA|
|DefaultTestAssemblyBuilder|No|No|Builds the test assembly|NA|
|NunitTestAssemblyRunner|Yes|No|Runs the test assembly|Add Run method, Use generic methods, Split public methods|
|TestProgressReporter|Yes|No|Reports progress of the test run|Add more handlers, add methods for other events|
|TestExecutionContext|Yes|No|The context of the test run|Add extra property|
|QueuingEventListener|Yes|Yes|Queues std events, hard bound|Add new similar class for custom events|
|EventQueue|No|Yes|The queue of events|Change to generic class|
|EventPump|Yes|Yes|Pumps events|Change to base class and derived class|
|SimpleWorkItemDispatcher|No|No|Dispatches work items|NA|
|WorkItem|No|No|The base class for work items|
|Event|No|Sure|Class for std NUnit events|Add another class for custom events|

