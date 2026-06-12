---
title: "MIME types"
date: 2014-09-06
forum: Ubuntu Studio
---

### Post by Ralph_French on 2014-09-06
Hi There, new to Ubuntu and Studio so please excuse my lack of understanding. I bought some software for screen writing ( FADEIN ) that uses the extension of .fadein. When I install it linked .fadein to ,zip files and Archiver. If I change the 'open with Fadein files it then trys to open .zip files with FadIn. On Linux Munt 17 I could have corrected this by editing /etc/mime.types and adding
 
```

application/x-dvi                dvi 
application/x-executable 

[COLOR=#0000ff]application/x-fadein-documents            fadein [/COLOR]

application/x-font                pfa pfb gsf pcf pcf.Z 
application/x-font-woff                woff 
```

And correcting any .zip references back to ARCHIVER.

Can someone help me do the same on UStudio? Thank you for any help.
Ralph

---

### Post by jejeman on 2014-09-06
Should be same as in mint. Personaly I use
.local/share/applications/mimeapps.list

---

### Post by Ralph_French on 2014-09-06
Jejeman, Good info thanks. The file was there all the time, I just was in too much of a hurry to get my system back up and functional. I think I like your idea better, thanks again.
Ralph

---

