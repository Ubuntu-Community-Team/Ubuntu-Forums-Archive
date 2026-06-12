---
title: "Bind Command Line Tool.."
date: 2007-08-02
forum: Server Platforms
---

### Post by Naatan on 2007-08-02
Hi.. I've been looking around for a command-line tool to manage a bind9 server, priimarely the zone files but if possible also the master file.

Ideally I should simply be able to add/delete A-records to my zone file.

I have found some tools but they all require way more setup than I would ideally expect, (eg. most of them would require me to reconfigure or heavily modify my current zone file setup)

Does anyone know a good tool for this?

---

### Post by HermanAB on 2007-08-02
Webmin handles bind OK.

Cheers,

Herman

---

### Post by Naatan on 2007-08-02
yea it does, but the reason I need a command line tool is so that I can write my own scripts, utilizing that tool.

---

### Post by koenn on 2007-08-02
there are some CLI admin tools (eg  rndc) but they operate on the daemin itself, not on the dns database (zone files, ..). 

Looks like if you want to manage zone files etc from a script, you'll just use the usual text editing tools : sed, awk, command output redirection, ...

---

### Post by HermanAB on 2007-08-02
You can try to modify the webmin scripts till they do what you want them to do.

---

