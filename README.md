# dicom4j
Dicom tools based on dcm4che3

### Examples

#### File Operations

```java
// read
DicomFile file = DicomFile.open("E:/test.dcm");
String patientName = file.dataset.getString(Tag.PatientName);

// write
file.dataset.setString(Tag.PatientName, VR.PN, "DOE^JOHN");
file.save("E:/test2.dcm");
```

#### File Convert

```java
// convert to image
DicomConvert convert = new DicomConvert("E:/test.dcm");
convert.toImage("E:/test.jpg");
convert.toImage("E:/test.png");
convert.toImage("E:/test.bmp");

// convert to json
convert.toJson("E:/test.json");

// convert to pdf
convert.toPdf("E:/test.pdf");
```

#### C-Echo SCP

```java
new DicomServer(11112, new BasicCEchoSCP()).start();  // alt1
new DicomServer("127.0.0.1", 11112, "PACS", new BasicCEchoSCP()).start();  // alt2
```
