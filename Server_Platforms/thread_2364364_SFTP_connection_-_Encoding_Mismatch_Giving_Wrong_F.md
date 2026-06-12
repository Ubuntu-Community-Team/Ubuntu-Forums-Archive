---
title: "SFTP connection - Encoding Mismatch Giving Wrong File Names"
date: 2017-06-22
forum: Server Platforms
---

### Post by natessh123 on 2017-06-22
I have a problem with a java SFTP connection to a file repository returning incorrect file names. I believe an incorrect encoding on the SSH installation on the AIX 7.1 system may be the culprit. Can anyone tell me a method to confirm the encoding in use by the SSH (or recommend another fix)? 
Example:
Correct: testmodel123±±±xyz.model
Displayed: testmodel123???xyz.model


The java code I'm using with the vfs 2.1 library is set up to use the  UTF-8 encoding when reading file names (using the SftpFileSystemConfigBuilder class setFileNameEncoding() method), but on one machine we consistently get errors where special characters are returned as "?"s, ultimately giving us the wrong names. Since on some other machines we're getting correct results, the solution must be elsewhere, specifically in the SSH installation itself, as this is showing that the name is reaching us with the wrong name before we have a chance in java to "ask for the UTF-8 version" of the file name, so to speak. 


To reiterate, we have two setups, both using Windows Server 2012 R2 Standard OS attempting an SFTP connection to different AIX 7.1 OS machines. In one case, the file names are returned correctly. In the other, we get incorrectly encoded file names (it seems). An SSH encoding issue seems like the likely culprit. Does anyone have any suggestions for possible solutions?

---

