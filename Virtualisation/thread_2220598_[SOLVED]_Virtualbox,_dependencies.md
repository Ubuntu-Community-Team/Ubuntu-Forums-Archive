---
title: "[SOLVED] Virtualbox, dependencies"
date: 2014-04-28
forum: Virtualisation
---

### Post by yan4 on 2014-04-28
I don't know what else I can do. I am just getting more and more frustrated after to spend a lot of time making updates and installs and the thing just doesn't work as it should.

:(

I started with Ubuntu 12.10 and VB 3.1.18 and it kind of worked (with a few glitches). The bigger latest glitch I had was that the 1920x1024 screen resolution just disappeared from the Windows 7 guest after it had there and worked fine. I tried a lot of solutions but couldn't get it back. Well, I guess that if I restart with a clean OS install it will work, but this is ridiculous and I simply refuse to do this. Anyway, someone has advised to try a more recent version of VB then I downloaded the vs 4.3.10 for U12.10 in the hope that it would solve my problems. Well, when I tried to process the .deb package I got this long list of missing dependencies:

dpkg: problemas com dependências impedem a configuração de virtualbox-4.3:
 virtualbox-4.3 depende de libc6 (>= 2.15).
 virtualbox-4.3 depende de libcurl3 (>= 7.16.2).
 virtualbox-4.3 depende de libdevmapper1.02.1 (>= 2:1.02.20).
 virtualbox-4.3 depende de libgcc1 (>= 1:4.1.1).
 virtualbox-4.3 depende de libgl1-mesa-glx | libgl1.
 virtualbox-4.3 depende de libpng12-0 (>= 1.2.13-4).
 virtualbox-4.3 depende de libpython2.7 (>= 2.7).
 virtualbox-4.3 depende de libqt4-network (>= 4:4.5.3).
 virtualbox-4.3 depende de libqt4-opengl (>= 4:4.7.2).
 virtualbox-4.3 depende de libqtcore4 (>= 4:4.8.0).
 virtualbox-4.3 depende de libqtgui4 (>= 4:4.8.0).
 virtualbox-4.3 depende de libsdl1.2debian (>= 1.2.11).
 virtualbox-4.3 depende de libssl1.0.0 (>= 1.0.0).
 virtualbox-4.3 depende de libstdc++6 (>= 4.6).
 virtualbox-4.3 depende de libvpx1 (>= 1.0.0).
 virtualbox-4.3 depende de libx11-6.
 virtualbox-4.3 depende de libxcursor1 (>> 1.1.2).
 virtualbox-4.3 depende de libxext6.
 virtualbox-4.3 depende de libxinerama1.
 virtualb
dpkg: error processing package virtualbox-4.3 (--install):
 problemas de dependência - deixando desconfigurado


OK, my very first thought is that my U12.10 could be outdated, then just to be sure that it wasn't an OS issue I downloaded an U14.04 ISO, burned it to DVD and installed it. After that I fully updated it.

Finally I downloaded a proper VB 4.3.10 deb package to U14.04. Since there is not yet an official release for U14.04 I downloaded the [COLOR=#000000][FONT=Verdana]U13.10 ("Saucy Salamander") [/FONT][/COLOR]one[COLOR=#000000][FONT=Verdana].

[/FONT][/COLOR]When I tried to process the .deb package, guess what: I got AGAIN the same long list of missing dependencies!!!!![COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]
Now I am really running out of options and have no idea what to do in the next. Very very very disappointed.

Anyone has an idea what can be done in such case?

:confused:

PS: And that's not all. Now, after the 'partial' installation I cannot install other softwares because it keep saying that VB must to be uninstalled first.

---

### Post by yan4 on 2014-04-28
OK, I made some progresses.

After to fail the install I ran:

*sudo apt-get -f install*

So it found a lot of missing packages and installed almost all the dependencies. Then I ran the deb package again and now it is complaining about only ONE dependency: **psmisc**.

I have installed the psmisc package (it says that it is installed and it's the newest version) but VB still keep saying that it is a missing dependency...

---

### Post by yan4 on 2014-04-28
OK, after a lot of head banging I just solved it with the most stupid solution:

1) I uninstalled the problematic package
2) Installed VB from the Software Centre

Apparently it is working (it starts) but I didn't try yet the Extension Package and neither to create a VM because is a bit late here and I am sick of computers for the day. Let's see what will happen tomorrow.

Anyway, I advice anyone to avoid the Oracle deb packages are they seem to be screwed.

---

