---
title: "Firewall issue when no firewall enabled ?"
date: 2016-01-18
forum: Security
---

### Post by oygle on 2016-01-18
Have been running speed tests from [http://www.speedtest.net/](http://www.speedtest.net/) - works fine. Our ISP has asked if we can run some speed tests from their website. Their speed test simply runs an ookla type speed test, but the ISP records the results. So here is the weird thing ...

1. Run ISP's speed test and always get this msg "Latency Test Error - Couldn't connect to the test server. A firewall could be blocking the connection or the server might be having some issues. Please try again later."  Using Kubuntu but no UFW running, it says "status inactive".

2. On the same computer, reboot to Win XP pro, and Run ISP's speed test - no errors, test runs fine.

3. On a laptop running Kubuntu, ran ISP's speed test - same error.

In both 1 and 2 above, the same computer, same modem/router (firewall set), but XP allows it to run, whereas Kubuntu doesn't. In fact I think that XP drive runs some sort of firewall.

So, one question is, does Kubuntu have 'firewall/security' layers by default ??

---

### Post by maxinstuff2 on 2016-01-18
If it is running in a browser, it's on port 80 or maybe another port if it's https (I can't remember which it is). In either case it should not be blocked by your firewall if general browsing works. Note that I am speaking now of the firewall on your ROUTER, not any software firewall you may or may not be running on your local machine. By default you should not have any software firewall running.

It could be that they are trying to specify a port in the URL, which your router is blocking by default, maybe in some misguided attempt to obscure the page they sent you to from the unwashed masses.

Can you tell me, does the url when you go to this page have a colon at the end followed by some numbers?
Eg (won't work, obviously): [www.speedtest.net:2222]("http://www.speedtest.net:2222")

IMO, most lilkely scenario is simply that their service isn't working atm. As per the error: "[COLOR=#000000]A firewall could be blocking the connection or **the server might be having some issues.** Please try again later."[/COLOR]

---

### Post by oygle on 2016-01-19
> **maxinstuff2 said:**
> If it is running in a browser, it's on port 80 or maybe another port if it's https (I can't remember which it is). In either case it should not be blocked by your firewall if general browsing works.

That depends on what the speed test is doing. Port 80 or 443 for https are outgoing. The speed test may be trying to access a port on my computer (incoming).

> **maxinstuff2 said:**
> It could be that they are trying to specify a port in the URL, which your router is blocking by default, maybe in some misguided attempt to obscure the page they sent you to from the unwashed masses.

That doesn't explain why I'm able to run the test from a Win XP Pro O/S, but not from a Kubuntu O/S (same router, same computer).

> **maxinstuff2 said:**
> 
Can you tell me, does the url when you go to this page have a colon at the end followed by some numbers?
Eg (won't work, obviously): [www.speedtest.net:2222]("http://www.speedtest.net:2222")

There is no port number in the url when I commence the speed test. Of course that isn't indicative of any port usage after that (i.e incoming).

> **maxinstuff2 said:**
> 
IMO, most lilkely scenario is simply that their service isn't working atm.

The service works fine for a Win pro O/S though.  :)

---

### Post by maxinstuff2 on 2016-01-19
If you have ruled out server-side issues, and your router, and this is all running in a browser, I would start looking at any plugins that it might be relying on.

If it isn't that, then your ISP needs to tell you what port this speed test is using. To my knowledge, a service running in a web page cannot use a port other than the one you used to connect to it (80) unless a separate service on their server is attempting to connect to you on another port, which would be VERY unusual.

Edit: if you are really stuck, and don't mind sharing the URL, I can try it. I am on kubuntu 14.04 so if its distribution specific it should also happen to me.

---

### Post by oygle on 2016-01-19
From [http://www.ookla.com/support/a22986756/Netgauge-Client-Error-Socket](http://www.ookla.com/support/a22986756/Netgauge-Client-Error-Socket)

Error Message - Latency Test Error - "Couldn't connect to the test server. A firewall could be blocking the connection or the server might be having some issues. Please try again later."

Resolution and Troubleshooting: - Latency Test Error - "A firewall could be blocking the connection or the server might be having some issues. The default ports used by NetGauge are TCP & UDP 8080, which needs to be open between the client and the server."

So, even though the initial access is port 80, the test uses port 8080. The router settings have remained in place, so it must be Kubuntu that is blocking ??

Regards sharing the URL. yes, I will send the URL, however if your IP is not one issued from the ISP, you will get a 403. I tried it via another connection.

[maxinstuff2]("http://ubuntuforums.org/member.php?u=1920572") replied after I tried telnet ..

> This tells me that there is a browser configuration issue. Maybe it relies on a plugin (flash most likely)? Is flashplayer installed?

Hmm, I do use the Firefox plugin "Shockwave Flash", version 11.2.202.559 , only updated the other day from [https://get.adobe.com/flashplayer/otherversions/](https://get.adobe.com/flashplayer/otherversions/)

Will the suggestion to do this ..

```
sudo apt-get install flashplugin-installer
```

..replace the FF plugin, or complement it ?  Looking at muon package manager, it is the same thing ?

---

### Post by maxinstuff2 on 2016-01-19
Complements it. 

All that package does is keep your flash plugin up to date.

I guess that leaves us in a spot of bother. It appears to be a browser specific issue. You could try manually installing the latest version of Firefox or you can install chrome just to check it (uninstalling when you are done if you don't want to keep it).

---

### Post by oygle on 2016-01-19
Okay thanks, I installed that package, speed test failed again. Ran SeaMonkey, same result, then realised SeaMonkey is sourced from Mozilla.  lol

If I right click near the "Begin test" button, then go to Global Settings, there are some messages.

[ATTACH=CONFIG]266839[/ATTACH]

---

### Post by SeijiSensei on 2016-01-19
I'm running Kubuntu 14.04 and I don't even have a /usr/lib64 directory, never mind /usr/lib64/kde4.  Do you?

Searching for kcm_adobe_flash on Google brings up this five year old thread: [https://forums.mageia.org/en/viewtopic.php?f=8&t=776](https://forums.mageia.org/en/viewtopic.php?f=8&t=776)

I doubt that Adobe applet even exists any longer.  I don't see it in my rather vanilla 14.04 installation, and I don't see any mention of it past that 2011 thread. Did you try to install Flash from the Adobe web site?  You should only rely on flashplugin-installer from the Ubuntu repositories.

---

### Post by maxinstuff2 on 2016-01-19
Ok, flash in mentioned in the error and then underneath it says you possibly have some orphaned modules. 

Please try purging flash completely and reinstalling. 

For this I would use synaptic (to make sure you dont miss anything). Just search for any flash packages and mark them for "complete removal".
Log out/in, then reinstall flashplugin-installer package. 

See if that fixes it.

---

### Post by oygle on 2016-01-19
> **SeijiSensei said:**
> I'm running Kubuntu 14.04 and I don't even have a /usr/lib64 directory, never mind /usr/lib64/kde4.  Do you?

Searching for kcm_adobe_flash on Google brings up this five year old thread: [https://forums.mageia.org/en/viewtopic.php?f=8&t=776](https://forums.mageia.org/en/viewtopic.php?f=8&t=776)

I doubt that Adobe applet even exists any longer.  I don't see it in my rather vanilla 14.04 installation, and I don't see any mention of it past that 2011 thread. Did you try to install Flash from the Adobe web site?  You should only rely on flashplugin-installer from the Ubuntu repositories.

I do have a /usr/lib64/kde4 path, here it is ..

[ATTACH=CONFIG]266841[/ATTACH]

and yes, I have been installing Flash from the Adobe website. So, I have the Adobe website .so file, I have the Firefox plugins "Shockwave Flash" and I have done this today ...

```
sudo apt-get install flashplugin-installer
```

How do I get rid of it all, and only install what I should, please ?

---

### Post by SeijiSensei on 2016-01-19
Firefox determines which plugins to use by consulting the directory /usr/lib/mozilla/plugins.  What links do you see there?

I'm loathe to offer help with this problem because I'm using the Windows version of Flash plugin via [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html").  So I don't have the ordinary Ubuntu flash plugin either.

---

### Post by maxinstuff2 on 2016-01-19
I like to use synaptic package manager for this. Synaptic is basically a GUI front end for apt-get. It's much easier than using terminal when you are trying to hunt things down. 

```
sudo apt-get install synaptic
```

Then in synaptic you can search for "flash" and then click "installed packages" on the left and you should get every installed flash package. 
Mark them all for complete removal.

---

### Post by oygle on 2016-01-19
> **SeijiSensei said:**
> Firefox determines which plugins to use by consulting the directory /usr/lib/mozilla/plugins.  What links do you see there?


```

:/usr/lib/mozilla/plugins$ ls -al
total 8
drwxr-xr-x 2 root root 4096 Jan 20 12:17 .
drwxr-xr-x 3 root root 4096 Nov  1 10:14 ..
lrwxrwxrwx 1 root root   37 Jan 20 12:17 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   41 Mar 27  2015 libnpgoogletalk.so -> /opt/google/talkplugin/libnpgoogletalk.so
lrwxrwxrwx 1 root root   34 Mar 27  2015 libnpo1d.so -> /opt/google/talkplugin/libnpo1d.so

```

there is also /usr/lib/firefox/plugins and /usr/lib/firefox-addons/plugins ??

> **maxinstuff2 said:**
> I like to use synaptic package manager for this...

Yes, I've always used synaptic PM

Well, I removed flash, and even removed Firefox for a good measure. Reinstalled FF and the Kubuntu flash , but same error ocuurs.  lol

---

### Post by maxinstuff2 on 2016-01-19
You logged out and back in afterwards?

telnet works, so you can connect, they aren't stopping you based on your OS. The error you are getting on the web page is a lie.
IMO it is a browser or browser config issue.

Without installing another (non-Mozilla) browser however, we wont be able to confirm or deny that. 
If you find the idea of installing chrome distasteful, you could try Konqueror or Rekonq - both are native KDE web browsers. Make sure flash plugin is enabled in their settings and try it.

I reckon it will work. If it doesn't, and we don't get a more informative error, then I'll be out of ideas :)

---

### Post by oygle on 2016-01-19
Thanks for your reply. Installed Konqueror, plugins activated, tried speed test, ..same error.

---

### Post by maxinstuff2 on 2016-01-19
Do you get anything of interest in a terminal if you run firefox from there?

---

### Post by oygle on 2016-01-20
> **maxinstuff2 said:**
> Do you get anything of interest in a terminal if you run firefox from there?

1. If I just do a bit of browsing and then exit, the terminal output is

> 
$ firefox &
[1] 6465
*******@home:~$ 
[1]+  Done                    firefox
*******@home:~$ 


2. If I go to the speed test site ..

> 
$ firefox &
[1] 6581
******@home:~$ Vector smash protection is enabled.
Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: No such file or directory


Some googling, seems that message is for a game. 

Noticed when run from the terminal, the speed test site very quickly displayed something. Too fast to read. I'm using the Nouveau display driver.

---

### Post by maxinstuff2 on 2016-01-20
Does the same error occur when using other flash based sites?

From what I can tell that error is very normal but you could try loading the proprietary Nvidia drivers to see if it changes.

---

### Post by oygle on 2016-01-20
The one factor that is different between the Win O/S and the Kubuntu O/S is that the Win box would be using the NVidia drivers (albeit old). I'm not going to fiddle around getting the proprietary Nvidia drivers working though.

---

