---
title: "Replace self signed SSL with a purchased SSL"
date: 2013-06-05
forum: Security
---

### Post by vecon on 2013-06-05
Hi,

I am new to this area.  I am working on ActiveCollab, which is currently using self-signed SSL.
How do I go about replacing the self-signed SSL with the one I will purchase (not so sure about how to generate the CSR either)?
Can anyone give me a step by step instruction on how to get this done?

Thank you very much!

---

### Post by bswilson on 2013-06-05
I'm not an expert with ActiveCollab, but I did a little Google research on what it is. It appears that this is a hosted application that runs on NGINX. Are you hosting this with a provider like GoDaddy or 1&1 or something? If you have this on a standalone server that you manage, I would think you can follow any Google-based process on generating a CSR from within Apache or NGINX. There's a good configuration example here ([https://gist.github.com/pixelDanny/2552976](https://gist.github.com/pixelDanny/2552976)) that seems to show how to modify the ActiveCollab config once you get there.

---

### Post by 2Stoned on 2013-07-08
What kind of server software are you using? If we don´t know what you are using we can´t really help you. Anyway, to create CSR file from the command line: 
```
openssl req -newkey 2048 -nodes -keyout YOURKEYfile.key -out REQUEST.csr
```

Open REQEUST.csr with your favorite text editor. Copy the code/text 
&#8212;&#8211;BEGIN CERTIFICATE REQUEST&#8212;&#8211;
..
&#8212;&#8211;END CERTIFICATE REQUEST&#8212;&#8211;

and use it for requesting a signed certificate.

---

