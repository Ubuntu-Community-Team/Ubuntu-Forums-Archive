---
title: "Am I infected?"
date: 2010-08-17
forum: Security
---

### Post by vratnica on 2010-08-17
Yesterday I was stupidly acting as a brave Linux user, claiming that no virus could harm me. So I visited the site <snip> which was reported as a harmful site...

after restart I couldn't log in anymore. Actually, what happens is that I get login screen, I log in, then I see my Desktop and then again the black screen. After that I continuously get black screens and some messages from my monitor, one after another

I can only login by GNOME Failsafe...

Anyone can help?

Please...

---

### Post by wacky_sung on 2010-08-17
I am not so sure how you got affected but very likely is that you got infected with it.Cleared all your cache / browser cookies ,etc and reboot again to verify.

---

### Post by FuturePilot on 2010-08-17
Did you continue past the warning page? What are the messages that you are seeing pop up?

---

### Post by uRock on 2010-08-17
If you want to troubleshoot, then that is fine, but I would never trust a compromised system.

---

### Post by vratnica on 2010-08-17
yes I continued past the warning page. Then I have seen the website, although a little bit changed, without images loaded, a little bit mess was there, but I didn't see any pop-up

so @wacky_sung, you propose me to clear cache and cookies of my FF during the Failsafe session, and that should allow me to solve the problem of log in?

---

### Post by CharlesA on 2010-08-17
Sounds like X had a problem tbh.

---

### Post by FuturePilot on 2010-08-17
I doubt that it was some drive-by malware that did that. Sounds unrelated honestly.

---

### Post by vratnica on 2010-08-17
hmmmm

so what to do?

---

### Post by cariboo on 2010-08-17
Check /var/log/Xorg.0.log, to see what the problem with Xorg is.

---

### Post by CharlesA on 2010-08-17
My bet is that flash caused X to take a dump, but it's just a guess.

---

### Post by wacky_sung on 2010-08-17
> **vratnica said:**
> yes I continued past the warning page. Then I have seen the website, although a little bit changed, without images loaded, a little bit mess was there, but I didn't see any pop-up

so @wacky_sung, you propose me to clear cache and cookies of my FF during the Failsafe session, and that should allow me to solve the problem of log in?

I will suggest you to clear your firefox & flash cache and cookies.Most malwares / script trojan usually residual their code down there,otherwise you may execute some files from the site.If you run Ubuntu dual boot with Microsoft OS and it can contribute to this issue.

---

### Post by xircon on 2010-08-17
Most malware is aimed at Windows, this sounds unrelated to me.  Boot off a live CD and check your logs.  Did you install or update anything around the same time?

---

### Post by vratnica on 2010-08-17
ok :)

I updated now the machine (forced) and there is no problem anymore :)

Thank you all guys who tried to help me

---

### Post by vratnica on 2010-08-17
> **xircon said:**
> Most malware is aimed at Windows, this sounds unrelated to me.  Boot off a live CD and check your logs.  Did you install or update anything around the same time?

nothing. but I can run it also with GNOME Failsafe

---

### Post by uRock on 2010-08-17
> **vratnica said:**
> nothing. but I can run it also with GNOME Failsafe
I would put money on whatever java scripting was on that site made an adjustment to xorg, as previously mentioned. It would be simple for a site to recognize that you were running Linux and to run the proper java scripting to attack your system.

Before going to such sites again I'd suggest getting AppArmor running and install the NoScript add-on in Firefox.

---

### Post by FuturePilot on 2010-08-17
> **uRock said:**
> I would put money on whatever java scripting was on that site made an adjustment to xorg, as previously mentioned. It would be simple for a site to recognize that you were running Linux and to run the proper java scripting to attack your system.

Before going to such sites again I'd suggest getting AppArmor running and install the NoScript add-on in Firefox.

I don't even think JavaScript can change something like X. I went to the site in question in a VM using Firefox with no extensions installed and ignored the warning. Afterwards I rebooted the VM and everything was still fine. This problem is most likely unrelated to viewing that website.

---

### Post by wacky_sung on 2010-08-17
> **FuturePilot said:**
> I don't even think JavaScript can change something like X. I went to the site in question in a VM using Firefox with no extensions installed and ignored the warning. Afterwards I rebooted the VM and everything was still fine. This problem is most likely unrelated to viewing that website.

Exploits can do almost anything.If you don't believe me, [click here]("http://go2.wordpress.com/?id=725X1342&site=irsdl1.wordpress.com&url=http%3A%2F%2F0me.me%2Fdemo%2Fcrowzers%2Firsdl%2Fhalt.html&sref=http%3A%2F%2Firsdl1.wordpress.com%2F2010%2F06%2F30%2Fcrowzers-or-carzy-browsers%2F") for a crash test dummy of your Firefox even with the latest 3.6.8.

Caution:Do it at your own risk(i have posted the link on another post before)

Which Browsers?
  - Mozilla Firefox 3.6.6: Halted with Mozilla Crash Reporter
  - IE7: Halted
  - IE8: Halted
  - Safari 5: Crashed on “javascriptcore.dll”

---

### Post by FuturePilot on 2010-08-17
> **wacky_sung said:**
> Exploits can do almost anything.If you don't believe me, [click here]("http://go2.wordpress.com/?id=725X1342&site=irsdl1.wordpress.com&url=http%3A%2F%2F0me.me%2Fdemo%2Fcrowzers%2Firsdl%2Fhalt.html&sref=http%3A%2F%2Firsdl1.wordpress.com%2F2010%2F06%2F30%2Fcrowzers-or-carzy-browsers%2F") for a crash test dummy of your Firefox even with the latest 3.6.8.

Caution:Do it at your own risk(i have posted the link on another post before)

Which Browsers?
  - Mozilla Firefox 3.6.6: Halted with Mozilla Crash Reporter
  - IE7: Halted
  - IE8: Halted
  - Safari 5: Crashed on “javascriptcore.dll”

Javascript crashing a browser is one thing, reconfiguring/breaking X is another.

---

### Post by wacky_sung on 2010-08-17
> **FuturePilot said:**
> Javascript crashing a browser is one thing, reconfiguring/breaking X is another.

I must said it depend on the type of exploit running it.Misconfiguration can contributed to the cause as well.Both are possible.

---

### Post by FuturePilot on 2010-08-17
> **wacky_sung said:**
> I must said it depend on the type of exploit running it.Misconfiguration can contributed to the cause as well.Both are possible.

Unless there was an exploit that allowed for privilege escalation and the ability to execute commands locally through the browser using some malicious JavaScript, then there is no way that JavaScript can interact with the system in a way that would break X.

---

### Post by wacky_sung on 2010-08-17
> **FuturePilot said:**
> Unless there was an exploit that allowed for privilege escalation and the ability to execute commands locally through the browser using some malicious JavaScript, then there is no way that JavaScript can interact with the system in a way that would break X.

Indeed you are right.Most of the exploits i have encountered for browsers are using javascript.If you can disable the use of java and flash then you are pretty safe from any malicious attacks that include exploit found within the java / flash player itself.

---

### Post by bodhi.zazen on 2010-08-17
> **FuturePilot said:**
> Unless there was an exploit that allowed for privilege escalation and the ability to execute commands locally through the browser using some malicious JavaScript, then there is no way that JavaScript can interact with the system in a way that would break X.

> **wacky_sung said:**
> Indeed you are right.Most of the exploits i have encountered for browsers are using javascript.If you can disable the use of java and flash then you are pretty safe from any malicious attacks that include exploit found within the java / flash player itself.

The problem / concern I have always had, there are potential firefox exploits.

Search this page for firefox or xulrunner :

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Which leads rapidly to:

[http://www.ubuntu.com/usn/usn-957-1](http://www.ubuntu.com/usn/usn-957-1)

> Several flaws were discovered in the browser engine of Firefox. If a user were tricked into viewing a malicious site, a remote attacker could use this to crash the browser or possibly run arbitrary code as the user invoking the program.

Lower down in the second link (emphasis added by me):

> A flaw was discovered in the Firefox **[color=darkred]JavaScript**[/color] engine. If a user were tricked into viewing a malicious site, a remote attacker code execute arbitrary JavaScript with chrome privileges. (CVE-2010-1215)

So you are both correct :twisted:

There is the potential for exploits, and it then depends on the payload and skill of the would be cracker.

So ...

I use NoScript + an apparmor profile for my browser.

---

### Post by uRock on 2010-08-17
> **FuturePilot said:**
> I don't even think JavaScript can change something like X. I went to the site in question in a VM using Firefox with no extensions installed and ignored the warning. Afterwards I rebooted the VM and everything was still fine. This problem is most likely unrelated to viewing that website.
Do you have AppArmor configured for FF in your VM?

---

### Post by FuturePilot on 2010-08-17
> **uRock said:**
> Do you have AppArmor configured for FF in your VM?

No.

---

### Post by wacky_sung on 2010-08-18
> **bodhi.zazen said:**
> The problem / concern I have always had, there are potential firefox exploits.

Search this page for firefox or xulrunner :

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Which leads rapidly to:

[http://www.ubuntu.com/usn/usn-957-1](http://www.ubuntu.com/usn/usn-957-1)



Lower down in the second link (emphasis added by me):



So you are both correct :twisted:

There is the potential for exploits, and it then depends on the payload and skill of the would be cracker.

So ...

I use NoScript + an apparmor profile for my browser.

I will recommended you to use Chromium as alternative browser.

_**My personal point of view**_
Firefox - Due to it popularity in the market as an alternative to window IE, it has now become the apple of cracker eyes.It has a fast and good update but lately the patches have seem to have slow down for patching those low security flaws found in the recent years.

Opera - People moved to Opera for it speed and low memory usage as compared to firefox.Opera often slow in patching their security patches as compare to firefox,unless a sever / middle security flaws have been found.

Chromium - Known to secure as compare to Firefox / Opera which so far nobody has used it in the blackhat conference.Beside that, google has offered to [pay]("http://blog.chromium.org/2010/01/encouraging-more-chromium-security.html") anybody who found bugs (flaws) 2x the amount of mozilla.

**_Conclusion_**
Flaws found in browsers will never cease,therefore it is always been a good security practice for me to use 2 to 3 alternative browsers to reduce the risk of being a potential target.

---

### Post by bodhi.zazen on 2010-08-18
> **wacky_sung said:**
> I will recommended you to use Chromium as alternative browser.

Chromium has it's own set of irritants and there are some security concerns with chromium as well. I do not like the way chromium handles passwords.

And what makes you think I use firefox ?

---

### Post by uRock on 2010-08-18
> **wacky_sung said:**
> I will recommended you to use Chromium as alternative browser.

_**My personal point of view**_
Firefox - Due to it popularity in the market as an alternative to window IE, it has now become the apple of cracker eyes.It has a fast and good update but lately the patches have seem to have slow down for patching those low security flaws found in the recent years.

Opera - People moved to Opera for it speed and low memory usage as compared to firefox.Opera often slow in patching their security patches as compare to firefox,unless a sever / middle security flaws have been found.

Chromium - Known to secure as compare to Firefox / Opera which so far nobody has used it in the blackhat conference.Beside that, google has offered to [pay]("http://blog.chromium.org/2010/01/encouraging-more-chromium-security.html") anybody who found bugs (flaws) 2x the amount of mozilla.

**_Conclusion_**
Flaws found in browsers will never cease,therefore it is always been a good security practice for me to use 2 to 3 alternative browsers to reduce the risk of being a potential target.
Firefox with NoScript and a well set AppArmor do fine. 

Google offers twice the money because they know Mozilla is ahead of them. I can name a few sites that do not work with Chrome(ium).

---

### Post by TwoEars on 2010-08-23
After taking a look at the source coder for the related site, I can confirm that unless they changed the Javascript, then there not a single piece of malicious code on that website. Even if there was, no damage could possibly be done to x config files unless you do something ridiculous, such as run Firefox as root.

---

### Post by vratnica on 2010-08-25
I came to that conlusion as well :) since I had this problem again, this time without visiting any strange site, and the problem was than fixed again the same way- by forcing the update

---

### Post by vratnica on 2010-09-06
well, the problem isn't solved actually :rolleyes:

I still have the same problem, and it actually never stopped. But it does not occur always but sometimes- in about half of all boots.

secondly, it also happens when the PC isn't active for longer time- so the monitor locks. When I try to lift the lock, the same happens: the combinations of black screen and the siemens-fujitsu logo...

the most strange thing is that, if the problem occurs on the start, i catch to see my desktop before the black screen...

---

### Post by OpSecShellshock on 2010-09-06
Looks like it might be time to check for problems with the video hardware then.

---

### Post by vratnica on 2010-09-07
video hardware? What's that?

---

### Post by fintos on 2010-09-07
There is no chance of virus to enter Linux platform. In my opinion may be some software files get corrupted or may when your machine become dual booting system such type of problems may occur there.

---

### Post by OpSecShellshock on 2010-09-07
> **vratnica said:**
> video hardware? What's that?

Oh sorry, misspoke. I meant graphics hardware. Problems there could cause trouble getting a graphical desktop session going.

---

### Post by vratnica on 2010-09-07
but I actually get the graphical session, I first see my desktop with icons for a second, and only after that a black screen...

---

### Post by uRock on 2010-09-07
> **fintos said:**
> There is no chance of virus to enter Linux platform.
Not true.

Just because there are no known viruses in the wild, doesn't mean there isn't any and it definitely doesn't mean Linux is immune to them.

---

### Post by cariboo on 2010-09-07
> **vratnica said:**
> but I actually get the graphical session, I first see my desktop with icons for a second, and only after that a black screen...

That's usually an indication that you don't have your graphics hardware set up properly, it has nothing to do with malware.

---

### Post by Rubi1200 on 2010-09-07
> **vratnica said:**
> but I actually get the graphical session, I first see my desktop with icons for a second, and only after that a black screen...
If this is a graphics problem, and it is starting to sound like it, then we need to know what graphics card you have installed please.

Go to the terminal (Applications > Accessories) and post the output of this
```
lspci | grep VGA
```

---

### Post by vratnica on 2010-09-07
-desktop:~$ lspci | grep VGA
05:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1950 GT (rev 9a)

---

### Post by Rubi1200 on 2010-09-07
I don't use ATI but you might want to check if there are any updates available for it:

System > Administration > Hardware Drivers

If that doesn't help, I suggest starting a new thread in General Help and seeing if someone can offer a solution for your particular graphics.

---

### Post by vratnica on 2010-09-07
I get the message: "No propriatary drivers are in the use on this system"

but the desktop effects are working by me perfectly...

...when I log in regularly and not as "Failsafe GNOME"

---

