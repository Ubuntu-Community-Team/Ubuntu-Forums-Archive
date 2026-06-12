---
title: "Apache and MimeType"
date: 2009-09-30
forum: Server Platforms
---

### Post by Svarten on 2009-09-30
Hiya,

I recently installed a web server to host our users privet homepages.

We NFS mount the windows homediretories read-only and configured userdir module to read from that disk, that much is working fine, BUT I am trying to force apache to give even plain text a download dialogue for everyone serverside.

```

<IfModule mod_userdir.c>
        UserDir /wwwhome/*/public_html
        UserDir disabled root

        <Directory "/wwwhome/*/public_html">
                EnableMMAP Off
                EnableSendfile Off
                AllowOverride All

                # Default to octet-stream i.e. binary file.
                DefaultType application/octet-stream

                # Binary files
                AddType application/octet-stream obj bin exe dll

                # Force Download on text files.
                AddType application/force-download txt text log asc mp3 m3u lst
                AddType application/force-download TXT TEXT LOG ASC MP3 M3U LST

                # MimeType for PDF files.
                AddType application/pdf pdf

                # Microsoft Documents
                AddType application/msword doc dot
                AddType application/vnd.ms-excel xls
                AddType application/vnd.ms-powerpoint ppt pps
                AddType application/vnd.ms-project mpp
                AddType application/vnd.openxmlformats docx pptx xlsx

                # Mobile applications
                AddType application/octet-stream sisx
                AddType application/vnd.symbian.install sis
                AddType application/java-archive jar
                AddType application/x-java-archive jar
                AddType text/vnd.sun.j2me.app-descriptor jad

                # Compressed files
                AddType application/x-rar-compressed .rar
                AddType application/zip .zip
                AddType application/x-compress .Z
                AddType application/x-gzip .gz .tgz

        </Directory>
</IfModule>

```Now it seems that apache don't really care all that much what I try to do I tried telling it to send text/plain on .exe and it didn't care much about that ether.

So I am wondering what am I missing here, I'v tried both 
```
AddType application/force-download txt text log asc mp3 m3u lst
```and
```
AddType application/octet-stream txt text log asc mp3 m3u lst
```nothing seems to work :/

Any help appriciated!

---

