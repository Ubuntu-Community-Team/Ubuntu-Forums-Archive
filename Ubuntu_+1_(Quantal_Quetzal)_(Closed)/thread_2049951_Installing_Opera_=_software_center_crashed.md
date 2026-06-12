---
title: "Installing Opera = software center crashed"
date: 2012-08-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by GreatDanton on 2012-08-29
I tried to install latest Opera which I downloaded from official site. When I double clicked on .deb file I got some errors, and software center crashed. Look at the attached images. It seems that this is known bug: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1041205](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1041205)  

Does anybody has the same problem?

 Also I am interested in the first message. What does it mean? Is the package really bad quality or is this just because latest opera is not compatible with Quantal Quetzal?  
  
Regards.

---

### Post by kyleabaker on 2012-08-29
This happens for Opera debs during this stage of Ubuntu dev every single cycle. I've seen the same error.

To get around it for now, if you've not found a way yet, you can just install Opera via the follow in a terminal:

```
sudo dpkg -i <path-to-opera-deb>
```

---

### Post by GreatDanton on 2012-08-30
Yes that solve this. It seems that Opera it's still under development =).

---

### Post by fyfe54 on 2012-08-30
> **kyleabaker said:**
> This happens for Opera debs during this stage of Ubuntu dev every single cycle. I've seen the same error.

To get around it for now, if you've not found a way yet, you can just install Opera via the follow in a terminal:

```
sudo dpkg -i <path-to-opera-deb>
```

I have been using the Opera development releases too, and have never had problems installing using the above code.

---

### Post by stinkeye on 2012-08-30
Opera running fine here.
PS. I tend not to use the software centre and install synaptic and gdebi
to install deb downloads. Set gdebi as the default application for Debs by right clicking on a Deb and choosing gdebi in
properties > Open With.

---

### Post by mc4man on 2012-08-30
> **GreatDanton said:**
> 

 Also I am interested in the first message. What does it mean? Is the package really bad quality or is this just because latest opera is not compatible with Quantal Quetzal?  
  
Regards.
Next time that happens, if interested in why click on the "Details" & it should show which lintian test(s) it failed on.

---

### Post by GreatDanton on 2012-08-30
I was curious so I decided to reinstall Opera. I clicked on the details and this is the output:
```
Lintian check results for /home/jan/Downloads/opera_12.01.1532_i386.deb:
```

Regards.

---

### Post by mc4man on 2012-08-30
> **GreatDanton said:**
> I was curious so I decided to reinstall Opera. I clicked on the details and this is the output:
```
Lintian check results for /home/jan/Downloads/opera_12.01.1532_i386.deb:
```

Regards.
guess it didn't fail any, just another current isn't working quite right..

If you were to install google-chrome you'd get the popup - in this case it would fail one test - 

"Lintian check results for /home/doug/Downloads/google-chrome-stable_current_amd64.deb:
E: google-chrome-stable: file-in-etc-not-marked-as-conffile etc/cron.daily/google-chrome"

---

### Post by kyleabaker on 2012-08-30
> **GreatDanton said:**
> Yes that solve this. It seems that Opera it's still under development =).

I'm not seeing Opera painting issues. See attached screenshot, but I'm also using my [Ambiance skin for Opera]("http://www.kyleabaker.com/downloads/opera/skins/opera-standard-ambiance/opera_standard_ambiance_maverick_20120326.zip") to make it blend a little more smoothly. [[skin details]("http://kyleabaker.com/2010/05/26/ambiance-skin-and-speed-dial-backgrounds/")]

[IMG]http://img831.imageshack.us/img831/3279/43254599.png[/IMG]

---

### Post by GreatDanton on 2012-08-30
I installed your theme, but it doesn't look like yours =) and there is still that problem like before. It doesn't really matter since I am now using Firefox 15 and I am quite happy with it. I will wait till the official release of 12.10 and then try Opera again. So for now I think this can be marked as Solved even if it's not completely solved =).

Regards.

---

