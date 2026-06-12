---
title: "no hud and other problems - my unity is broken??"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jonasan Cope on 2012-03-02
Hey all,

I did a fresh install of 12.04 yesterday. Unfortunately Unity seems to be broken on my system. The dash seems to work ok but i have no HUD, and the program switcher looks like something from XP.

I have an ATI mobility graphics card which i thought might be an issue, but the propriety driver installed and seems to function ok.

also CCSM seems to little or nothing as well. pretty much all of the options seem disabled.

I have tried some things to get the latest version of unity from the unity-team ppa but wth no luck.

having installed the ppa, apt-get gives me the following errors after checking everything else fine. My internet is working fine.

W: Failed to fetch [http://ppa.launchpad.net/unity-team/hud/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/unity-team/hud/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/unity-team/hud/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/unity-team/hud/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/unity-team/hud/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/unity-team/hud/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

anyone experience something similar? or have any ideas on my problem and how to go forward?

thanks in advance

---

### Post by Jonasan Cope on 2012-03-02
ok, things move on, the update manager finally loaded the ppa so maybe things are looking up.

rebooted now and the hud exists! running unity testing now...

---

### Post by emt_1 on 2012-03-02
Well I too have no hud and no lenses and every time I right click to copy the panel and launcher disapear and desktop freezes,a result of todays update.Did mange to get a theme and some panel apps installed.Also having many problems with just about all the ppa,s now for unity.

---

### Post by rburkartjo on 2012-03-02
hud is not working on my end also. see what happens with updates. running unity 2d

---

### Post by Jonasan Cope on 2012-03-02
seems i am running unity 2d as well - though now i have the (fantastic) hud. I think my machine should be up to 3d though. Checking around i came up with this for checking support for 3d

/usr/lib/nux/unity_support_test -p

but when i run it i get


X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22

any thoughts?

---

### Post by Jonasan Cope on 2012-03-02
no running 3dwith hud, all is well - apart from that i had to disable my ati graphics card driver... but getting that to work is another issue. i'll try myself before posting.

sorry for the chatter...

and i love unity!

---

### Post by emt_1 on 2012-03-03
Well since yesterday and one new update today, things seem to have corrected themselves and everything seems to working including hud.One thing,would like to get the new lenses.ppa is listed in USC but USC can't find package,apt returns same message.

---

### Post by emt_1 on 2012-03-03
update manage to get ppa in sources and some lenses for Precise but not some older ones.Ran some testing and think things are looking good for beta.

---

