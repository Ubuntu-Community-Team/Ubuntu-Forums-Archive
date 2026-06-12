---
title: "Steganography using an MP3 file"
date: 2008-02-09
forum: The Cafe
---

### Post by DenKain on 2008-02-09
I am somewhat familiar with Steganography and the many applications available for Ubuntu when it comes to hiding information inside an image or a WAV file. What I have not been able to find is a Steganography program for Linux that will allow the user to hide information in an MP3 file. Is anyone familiar with such a program?

---

### Post by DenKain on 2008-03-15
bump

---

### Post by prshah on 2008-03-15
> **DenKain said:**
> I am somewhat familiar with Steganography and the many applications available for Ubuntu when it comes to hiding information inside an image or a WAV file. What I have not been able to find is a Steganography program for Linux that will allow the user to hide information in an MP3 file. Is anyone familiar with such a program?

MP3stego, steghide... [http://www.linux.com/articles/45440](http://www.linux.com/articles/45440)

Note that MP3 stego will only allow you to embed text files. So if you want to embed a binary file, maybe useful to uuencode that file first.

---

### Post by DenKain on 2008-03-15
Thank you very much.

---

### Post by chmdznr on 2008-05-12
Hi,
I have implemented another way to hide any type of file inside mp3 file without changing its size and sound quality.
It is different from mp3stego since my application directly access mp3 file(not wav file) per byte.
If you interested, you may check at my blog:
[http://achmadz.blogspot.com/2008/05/hide-any-file-inside-mp3-file.html](http://achmadz.blogspot.com/2008/05/hide-any-file-inside-mp3-file.html)

The downloaded file is including source code in Borland Delphi 7.

This application can run on Linux with wine installed.

---

### Post by leithon on 2010-04-11
I need help developing audio steganography application on java. Any advice? thanks in advance :)

---

