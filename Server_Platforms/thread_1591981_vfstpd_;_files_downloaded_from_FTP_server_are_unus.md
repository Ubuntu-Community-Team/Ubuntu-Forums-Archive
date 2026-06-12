---
title: "vfstpd :; files downloaded from FTP server are unuseable"
date: 2010-10-10
forum: Server Platforms
---

### Post by dwvm3 on 2010-10-10
Hello,

I have a very strange problem with vsftpd. I have set up vsftpd on  Ubuntu 10.04 32 Bit. Local users have access to their home directory  using their username and password to log in.

Users can upload files to the server and the files are OK. If I download  the same file, it is unuseable. The file size is the same than the  original file on the server, but the content is different. I tried many  FTP clients on Windows  and Ubuntu and set transfer mode to Auto and  Binary, but no success.

I examined the two different files in a Hex editor and it is clear that the content is not the same.

Here is a screenshot of the working file on the FTP server:

[IMG]http://www.control-nodes.com/Bilder/HexServer.png[/IMG]

This is the same File downloaded via FTP on the client:

[IMG]http://www.control-nodes.com/Bilder/HexClient.png[/IMG]

In the file from the client, the first 66 bytes are new:

00 21 70 B9 B3 D6 90 FB A6 47 6E EE 08 00 45 08 0B
84 06 60 40 00 40 06 00 00 C0 A8 01 65 C0 A8 01 06
DB 1B AE 33 A3 C9 8E B0 B1 59 33 46 80 10 00 5B 83
C2 00 00 01 01 08 0A 00 2F 88 D0 00 3F 7F E9


From byte 66 (0x42) the content equals with the start of the original file. But the 66 bytes are not only added to the beginning, because the total length of both files is equal. I also discovered that with files that are only 2kB the problem disappears, but a 4kB file has the same issue. To fit the original length, in the copied file from time to time a byte is skipped.

I could not find the complete byte sequence again, but the sequence 00 21 70 B9 B3 D6 90 FB A6 47 6E EE 08 00 45 appears a second time at byte 4344, and then every 2896 bytes again. To be sure that this is not a sequence that belongs to a frame header of the .mov file I did the same with a dll. And it was the same result. after the second occurence of the byte sequence, it repeats every 2890 bytes.


Thanks in advance

Dierk

---

### Post by dwvm3 on 2010-10-10
I tryed to set the trans_chunk_size=1024 hoping that this could solve the problem, but it doesn't. :(

---

