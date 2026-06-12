---
title: "Charset Encoding Ubuntu 8.04LTS"
date: 2011-05-03
forum: Server Platforms
---

### Post by khaled_jamel on 2011-05-03
I will explain my problem from the beginning, I have a ubuntu server 8.04LTS and I use a java application with Tomcat 6.0.18 and JRE 1.6, the problem that the display of character as (é è ç û) is replaced by other strange, I know this is a problem of character encoding so I try to add the encoding fr_FR.ISO-8859-1 in the bashrc file and /etc/default/locale and i added LANG="fr_FR.ISO-8859-1", i successfully display the good characters from a remote console (putty) but the same problem still by typing directly on the shell server.
for example mkdir a folder called "Août" I receive "Ao&#9830;t" :(
I think this may be due to the encoding used by the system partition but I do not know how I can verify this.
you have an idea why plz?
thank you

---

