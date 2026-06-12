---
title: "Ubuntu One Windows Client - Gathering Information, Please wait..."
date: 2012-02-13
forum: Ubuntu One (CLOSED)
---

### Post by jingaling on 2012-02-13
Hi guys,

I'm having some major issues with the Ubuntu One Client for Windows (UbO-W). The problem is that when I install UbO-W on my machine it asks me to either setup or login to an existing account. I enter my credentials and it the says "Gathering Information, please wait..." for around 30 minutes. I then get a prompt about taking a tour, I decline and then get the "gathering information" problem again.

After another 30 minutes or so I get the following error:

AttributeError
"'NoneType' object has no attribute 'get_rootdir'"

I close this error and it gives me the ubuntu one dashboard but nothing will sync and I can't add files & folders to my sync profiles.

I know this problem isn't to do with my UbO account as it's working fine on my multiple 11.10 boxes. I also know it's not my Windows box as I have tried it on 3 separate Windows boxes and all 3 have done exactly the same thing (2 where x64 and 1 was x86).

I've posted this problem on launchpad (link below) but I haven't had a reply as of yet so I thought I'd try here to get some help.

[https://bugs.launchpad.net/ubuntuone-client/+bug/930119]("https://bugs.launchpad.net/ubuntuone-client/+bug/930119")

Thanks guys,

Jing (Kev).

---

### Post by hildenbrandsteven on 2012-02-13
Try using the online (browser) method.

---

### Post by jingaling on 2012-02-13
Hi hildenbrandsteven,

That doesn't really help me as I need to be able to sync files to my Windows box. Downloading, changing and then uploading the file(s) manually simply wouldn't be feasible.

Kev

---

### Post by aquarius18 on 2012-02-13
Same problem here, it just hangs and won't go any further. :(

U1 version is 2.99.3 - downloaded yesterday and installed on a Win XP SP3 machine.

(U1 works perfectly for me in all my Ubuntu installs).

Need to add that my AVG is configured to allow U1 to connect to the internet, so that can't be the issue.....

---

### Post by AndiSG on 2012-02-14
Hello!

I had the same problem. I still don't know, why this problem occurred, but I think I managed to get it fixed, at least on my computer. Perhaps this works for you too.

The story is quite simple and goes like this: my firewall blocked the file C:\programs\ubuntuone\dist\ubunto-sso-login.exe. Just allow the file and everything is O.K. again!

---

### Post by jingaling on 2012-02-14
Hi Guys,

I've logged this with Ask Ubuntu and they came back to me and told me that U1 for Windows doesn't currently support Proxy servers. Now in work I use a proxy but at home I have a regular ADSL connection to a router and then out to the world. I knew about the proxy issue anyway and was prepared for the fact that it wouldn't work in the office. But at home it should work, but it doesn't.

I know it's not my firewall because if it was then my Ubuntu machines wouldn't work either. It's definitely something to do with the Windows client. Ask Ubuntu have asked for my log files so once they come back to me I will update you just in case it helps.

Kev

---

### Post by aquarius18 on 2012-02-14
> **jingaling said:**
> Hi Guys,

I've logged this with Ask Ubuntu and they came back to me and told me that U1 for Windows doesn't currently support Proxy servers. Now in work I use a proxy but at home I have a regular ADSL connection to a router and then out to the world. I knew about the proxy issue anyway and was prepared for the fact that it wouldn't work in the office. But at home it should work, but it doesn't.

I know it's not my firewall because if it was then my Ubuntu machines wouldn't work either. It's definitely something to do with the Windows client. Ask Ubuntu have asked for my log files so once they come back to me I will update you just in case it helps.

Kev

Thanks Kev - standing by for further developments. Thanks also to AndiSG for his hint - but as I mentioned earlier, AVG has been told to "let U1 through"

Frank

---

### Post by jingaling on 2012-02-14
Well I've now got it working. The Ubuntu One support guys basically said that they don't know what's happened and they have referred it to a developer. Anyway, they asked me to try an older version of the client and that worked for me. Here is a download link:

[http://one.ubuntu.com/windows/ubuntuone-2.0.3-windows-installer.exe](http://one.ubuntu.com/windows/ubuntuone-2.0.3-windows-installer.exe)

Good luck!

Kev

---

### Post by aquarius18 on 2012-02-15
> **jingaling said:**
> Well I've now got it working. The Ubuntu One support guys basically said that they don't know what's happened and they have referred it to a developer. Anyway, they asked me to try an older version of the client and that worked for me. Here is a download link:

[http://one.ubuntu.com/windows/ubuntuone-2.0.3-windows-installer.exe](http://one.ubuntu.com/windows/ubuntuone-2.0.3-windows-installer.exe)

Good luck!

Kev

Thanks for your advice Kev. This worked immediately for me, sync is happening as I type this :guitar: - guess version 2.99.3 for windoze has a mozzie (so-called bug)
Frank

---

### Post by hildenbrandsteven on 2012-02-15
Stop using ubuntu one and just setup OpenSSH on both systems.

---

### Post by jingaling on 2012-02-15
No problem Aquarius, glad it helped.

Kev

---

### Post by Malcolm_85 on 2012-10-27
After a long period of trouble free use, U1 died on my Windows Vista PC this week, I have tried all the various "solutions" in the forum to no avail.

I have tried re-installing with 3.0.2b, am able to log in and then whilst the 'files' tab or the 'settings' tab is selected I get the "Gathering info" message with the cycling orange ball. With the 'devices' or 'account info' tabs it shows the correct info and no cycling.
At one point (two nights ago) all of a sudden the 'synching files' logo popped up in the top right of the box and the PC synched up but when I powered up the next day, same problems again. "Could not connect to the syncdaemon ipc"

Any further suggestions? U1 is running fine on my Ubuntu PC's and this is really annoying not to synch with my windows box.

---

### Post by jingaling on 2012-10-27
Hi Malcolm,

It would be useful to know what "solutions" you have tried. Without this we may just be doubling up. Have you tried un-installing U1, clearing the cache and then re-installing?

There is also a help form within the U1 site once you're logged in. I've used it a few times and the guys there are extremely helpful and obviously know the product better than most.

Anyway, if you let us know what you tried then maybe we will be able to help. The same "gathering information" problem happened to me and clearing the cache fixed it.

---

