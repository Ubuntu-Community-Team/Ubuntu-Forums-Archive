---
title: "Parental Controls in Vista"
date: 2006-10-18
forum: Windows
---

### Post by kopilo on 2006-10-18
Hi I got some screen caps of the parental controls in Vista, so I thought I'd share them.

[Parental Controls Web Time]("http://www.gw4y.com/pgp/ParentalControls_Web_Time.jpg")
[Program Control access]("http://www.gw4y.com/pgp/ParentalControls_Program_Control.jpg")
[Web Controls]("http://www.gw4y.com/pgp/ParentalControls_Web_Access.jpg")
[Game Controls]("http://www.gw4y.com/pgp/ParentalControls_Game_Access.jpg")

Personally I find these fairly amazing and are wondering if there is anything like them in Ubuntu or in the pipeline for Ubuntu. (I use parent controls for vistors who use my computer, I don't have children)

---

### Post by elst on 2006-10-21
They do look interesting - Mac OS has at least some of these features, and I guess that Microsoft have copied them for Vista.

The Games control facility presumably relies on Windows-specific features. You can do the Web control features today on Linux by installing a proxy service on the machine - it would be good if Edubuntu was to include one by default, and I'll ask on the IRC channel about this. Edgy has a very basic desktop "lockdown editor", although it doesn't seem to block specific applications (it can block access to GNOME applets).

Remember that you can file a specification on Launchpad for developers to look at, and if you can present a good case then somebody may choose to work on implementing it.

---

### Post by kopilo on 2006-10-22
Well I'd imagine one way to control file access and execution such as in the ways of programs etc, would be through changing the file access preferences (such as with chmod). Of course this would primarily be a long drawn out static way of doing it.

---

### Post by elst on 2006-10-22
Yes, although file permissions would probably be the right mechanism for blocking individual executables it might be a bit fiddly and fragile to do directly. I think that the ideal would be for the administrator to be able to select applications in the same way that the "Open With" dialog works.

---

### Post by kopilo on 2006-10-23
Indeed, and maybe have an option list connected in Synaptic.

How's the IRC chat been going?

---

### Post by ago on 2006-10-26
I agree that it is extremely well designed. Kudos to Windows. 

But I think that we should aim for more.... 

Not just PC based access restriction, but a true Ubuntu-ZeroConf-HomeServer (spin-off of edubuntu). Possibly with a webinterface as nice and intuitive as the windows one.

"ZeroConf" in the sense that it uses ZeroConf and in the sense that it will work out of the box with reasonable settings. 
"Home Sever" in the sense that its main (plugin-based) functionality should be: 
[list][*] file server (indexed by tracker),
[*] printer server,
[*] multimedia streaming,  
[*] shared contacts, 
[*] shared calendar, 
[*] shared applications, 
[*] netinstall, 
[*] thinclient server, 
[*] firewall/gateway/proxy server with A/V and antispamming filters, 
[*] centralized access restrictions to machines/web/applications, 
[*] roaming of user profiles, 
[*] backend for MythTV or equivalent,
[*] one click backup to internal/external drive
[*] .... 
[/list]

All with a single, very easy to use web interface designed for inexperienced home users with only absolutely necessary options (for instance do not use groups, only users) and preconfigured with a reasonble setup. Make other Ubuntu installation "aware" of this server (domain master). This is useful today, also in homes that have clients from other OSs, or even for small businesses. It will become even more relevant in the near future when sub $100 machines like these [http://www.linutop.com/](http://www.linutop.com/) will become available and will be used as thin/fat clients and/or set-top boxes...

---

### Post by kopilo on 2006-10-26
wow that would be awesome. :D

---

### Post by ago on 2006-10-26
I started a thread in the cafe, if feedback is positive, it might be worth to make an official spec. I made a mockup interface in the 3rd post. All ideas welcome.

[http://www.ubuntuforums.org/showthread.php?t=284785](http://www.ubuntuforums.org/showthread.php?t=284785)

---

