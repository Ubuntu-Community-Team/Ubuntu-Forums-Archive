---
title: "Clamtk virus scanner found 6 &quot;viruses&quot; on my Ubuntu 9.10 system"
date: 2009-12-19
forum: Security
---

### Post by ahorriblemess on 2009-12-19
Seriously? I ran a check even though there's "no reason" to. They weren't really viruses I don't think... but they were in google chrome's cache. Here they are (assuming all files are in /home/me/.cache/google-chrome/Cache/...)

f_000bf
f_00069a
f_000419
f_000a43
f_0005c7
f_000931

Does anyone know what these really are?

---

### Post by Agent ME on 2009-12-19
What type of virus did it call them? Clam often labels certain javascript files as "PUA", which is short for Potentially Unwanted Application. In the case of PUAs found in a browser cache, these are often just harmless cached javascript files. I believe you can disable Clam from reporting these somehow.

---

### Post by ahorriblemess on 2009-12-19
Yea PUA, that's what it was. I didn't think it was anything serious since they were in my browsers cache. Are those the same as tracking cookies? I remember AVG in Windows has an option to scan for those.

---

### Post by cariboo on 2009-12-20
For more info on pua's, have a look [here]("www.sophos.com/support/knowledgebase/article/14887.html").

---

### Post by Dark_Stang on 2009-12-20
Likely just drive-by download files that only windows can get infected with. Common recent ones are "Green Antivirus", "Antivrus Pro", "Security Tool", "Driver Robot", etc. Nothing to worry about.

---

