# SetDeviceProperty {#reference_m2h_4rz_wdb .reference}

You can call this operation to set properties for a specified device. A successful result of calling this API only indicates that IoT Platform has successfully sent a property setting request to the device, but does not indicates that the device SDK has successfully received the request and performed the operation. Only if the device SDK responds to the request and sets the required property, you have successfully set the property for the device.

## Request parameters {#section_jgt_v2t_xdb .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action |String | Yes|The operation that you want to perform. Set the value to SetDeviceProperty.|
|IotId|string| No| The device ID.

 **Note:** If you specify this parameter, ProductKey and DeviceName are not required. IotId is the GUID. Each IotId corresponds to a combination of ProductKey and DeviceName. If you specify both IotId and the combination of ProductKey&DeviceName, the system follows IotId.

 |
|ProductKey|String| No| The product key of the device.

 **Note:** If you specify this parameter, DeviceName is required.

 |
|DeviceName|String| No| The device name.

 **Note:** If you specify this parameter, you must also specify ProductKey.

 |
|Items|String|Yes|For more information about the properties that you can set, see [Items](#table_omd_gft_xdb).|

|Name |Type|Description|
|:----|:---|:----------|
|key|String| The identifier of the property that you want to set. To view the property identifier of the Pro Edition device, go to the Define Feature page of the Pro Edition product that the device belongs to in the console.

 **Note:** You must specify a read-write property. This setting fails if you specify a read-only property.

 |
|value|Object|The property value. The property value, which must be within the data type and range of the property that you want to set.|

## Response parameters {#section_znb_2ft_xdb .section}

|Name |Type|Description|
|:----|:---|:----------|
|RequestId|String|The GUID generated by Alibaba Cloud for the request.|
|Success|Boolean |Indicates whether the call is successful. A value of true indicates that the call is successful. A value of false indicates that the call has failed.|
|ErrorMessage|String|The error message returned when the call fails.|
|Code|String|The error code returned when the call fails. For more information about error codes, see [Error codes](intl.en-US/Developer Guide (Cloud)/API reference/Error codes.md#).|
|Data|Data|The data returned when the call is successful. See the following table Data.|

|Name |Type|Description|
|:----|:---|:----------|
|MessageId|String|The ID of the message that IoT Platform sends to the device.|

## Examples {#section_n1g_xft_xdb .section}

**Request example**

```
https://iot.cn-shanghai.aliyuncs.com/?Action=setDeviceProperty
&ProductKey=al*********
&DeviceName=device1
&Items=%7B%22LightAdjustLevel%22%3A1%7D
&Common Request Parameters
```

**Response example**

-   JSON format

    ```
    {
      "RequestId":"57b144cf-09fc-4916-a272-a62902d5b207",
      "Success": true,
      "Data": {
    	  "MessageId":"abcabc123"
      }
    }
    ```

-   XML format

    ```
    <? xml version='1.0' encoding='utf-8'? >
    <SetDevicePropertyResponse>
        <RequestId>57b144cf-09fc-4916-a272-a62902d5b207</RequestId>
        <Success>true</Success>
        <Data>
    	 <MessageId>abcabc123</MessageId>
        </Data>
    </SetDevicePropertyResponse>
    ```


