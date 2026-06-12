---
title: "Likewise-Open ADDS Integration"
date: 2010-08-13
forum: Server Platforms
---

### Post by RS_Brooks on 2010-08-13
I setup Active Directory Domain Services on a Windows 2008 std box. I decided I'd try attaching to the internal domain I created with a 10.04LTS server build. I had originally planned to use open LDAP and Kerberos. However, after I saw a few news stubs and a short walk through on the Ubuntu site, I decided on Likewise-Open. Joining the domain was fairly straight forward and seemed to work fine. Unfortunately, I've had a rough time with Samba integration and Dynamic DNS updates on the MS DNS server. There is obviously some conflict in support between Samba and Likewise. Additionally, there seems to be some noise about Ubuntu packages of Likewise using the DDNS. All in all, it appears I'll need to dig in deeper to the issues if I want a stable Ubuntu member server in my domain. This leads me into my question, has anyone had any great success with this package on the 10.04 build? I'd appreciate any feedback that could be given before I start dumping time into troubleshooting the issues previously mentioned. Thanks much!

---

### Post by RS_Brooks on 2010-08-14
[COLOR=black][FONT=Verdana]Shocking. Not a single reply on this? Is this forum filling up with too many people like myself :P[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I still felt I should make a note on this thread in case some poor chump stumbles into the same mess. I got rid of LikeWise-Open and did all the configuration for ADDS authentication manually (basically just using Samba/Winbind, all I needed was Kerberos and OpenLDAP). Everything is working great now. I'll give Likewise-Open the benefit of the doubt and assume I had some dependencies goofed or config directives that were incorrect. I’m pretty good at fat fingering things. Nonetheless, there is a lesson to be learned here. I had taken a shortcut because I didn't want to dump a bunch of time into editing etc directive files. Yet in the end, I wasted almost 4X what was spent manually configuring the packages. In summary, I'll be watching my step before installing another "slam dunk" package. Final note, be careful if following any old “walk through” guides with this package, including the “officially supported Ubuntu Server Guide” unless you’re good at tracking down library dependencies.[/FONT][/COLOR]

---

