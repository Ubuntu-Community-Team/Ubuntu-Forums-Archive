---
title: "Samba - Group polies ?"
date: 2008-05-06
forum: Server Platforms
---

### Post by palin_linux on 2008-05-06
I have setup group polies for our samba domain using guide & many others
[http://www.pcc-services.com/custom_poledit.html](http://www.pcc-services.com/custom_poledit.html)

The question I have is how do I create a police to lock and start screensaver on windows xp after 15min using poledit? I have look all over and have found no reference to reg setting or poledit only Group polices.

Thanks for your help!!


Jeff 
Linux Admin

---

### Post by palin_linux on 2008-05-09
I was able to find a solution to this.\

If need you to do this with our PDC, here is a tar I put togather for you.

 In the tar there is:
Regpol. - [http://www.petri.co.il/software/regpol.zip](http://www.petri.co.il/software/regpol.zip)

REG FILE 
Turns on screen saver after 10min & login is required. Screen saver tab is grayed out.

logon.bat 
To run Regpol and import reg file. 

:)
Jeff

---

### Post by andguent on 2008-05-10
Thanks for posting back to the community to document this. It is the little snippets like this that make managing groups of Windows boxes that much easier.

Just as an FYI - a tool you might be inerested in is winexe. I had to compile it on my hardy server since the static binary didn't work, but it lets me force a windows box in the domain to run whatever commands I give it. It works great for silent installers and registry pokes.

---

