---
title: "Apache 2 / SSI - Unable to parse SSI files"
date: 2008-04-14
forum: Server Platforms
---

### Post by webwolf_3000 on 2008-04-14
Basically, I know this has been asked a thousand times before ;)

I had this working perfectly on my Apache1.x installation in windows, and Im absolutely sure everything is configured correctly, it just wont bloody work...

heres my confugerationables:

<Directory /http/>

Options Indexes FollowSymLinks MultiViews [B]+Includes
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml[/B]
AllowOverride None
Order allow,deny
allow from all

</Directory>


I do have the includes mod enabled - and basically, Includes do work - ie: .shtml files are included to the html files, but the SSI scripts dont parse.

so this " *<!--#echo var="DOCUMENT_URI"-->* " in a .shtml file would just not display at all.
or in the **<title>** *<!--#echo var="DOCUMENT_URI" -->* **</title>** sense, it literally displays:

" *<!--#echo var="DOCUMENT_URI" -->* "

confused... 

The .shtml files are set to chmod 755 so the permissions arent a problem.

Any ideas, It's drivin' me crazy... as always.

---

### Post by webwolf_3000 on 2008-04-14
Ok NM, I fixed it... ummm, dont know why, but as opposed to apache2 restart - apache2 force-reload seemed to resolve it - go figure.

I work on a helpdesk, You would think the first thing I would try is REBOOOOOTTTT!!!!!!!!! *tears hair out*

---

