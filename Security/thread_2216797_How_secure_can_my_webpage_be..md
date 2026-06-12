---
title: "How secure can my webpage be."
date: 2014-04-13
forum: Security
---

### Post by wlraider70 on 2014-04-13
i saw this link about using a raspberry pi to open your garage. 
[http://www.instructables.com/id/Raspberry-Pi-Garage-Door-Opener/](http://www.instructables.com/id/Raspberry-Pi-Garage-Door-Opener/)

so with that in mind, I would want a public webpage that can open my house to be quite secure.
Is there a better way that an old school username:password?

Can I use a public key method, like my ssh, to authenticate a webpage?

---

### Post by thnewguy on 2014-04-14
If you want the ability to open your house to be secure, then I would suggest not putting a method for opening your house on-line. Certainly not with a user-name and password. You could set up some sort of key method (a key is basically a long password). But I really don't think this is a good idea.

---

### Post by CharlesA on 2014-04-14
> **thnewguy said:**
> If you want the ability to open your house to be secure, then I would suggest not putting a method for opening your house on-line. Certainly not with a user-name and password. You could set up some sort of key method (a key is basically a long password). But I really don't think this is a good idea.

This. Even if the machine is only accessible via your wifi network, it could still be a security risk.

The same can be said for garage door openers that use radio frequencies, but only you will know when convenience is more important than security.

---

### Post by RadicaX on 2014-04-14
That will always be the problem with security online. More people have access to it. And to mess with it. Nothing is perfectly safe in this world, Period. passwords can help, and having the page not accessible by basic search engines would help too. (Though if someone found it through say something like the Deep net, odds are they know a bit more about computers). So there are a few things you can do... 

But think about it this way, without internet, there are still people that break into houses, you can have a moat, a draw bridge, and the key in three parts, it is still possible to break in. (Though with such security, it is very unlikely). The more ways you have to get in your house, the more ways it can be exploited. Having less ways to access your house, means less of a guessing game when someone does break in. More chances they have to play to your game.

So no, there is not perfectly secure way to do it, but if you are going to do it, do things to help your security, passwords are not super great, especially because they have to go somewhere. Encryption methods can help this, like SSL... But we have seen what just happened with the Heartbleed bug. Heck, it at this point probably would be safer just to do a RadioWave, a Signal not used often on a switch, can it be copied? Yes! Can someone by mistake come about such a frequency? Yes! Will it happen? Maybe, maybe not. Is it more secure than allowing it to be found than say the internet? Probably, but it might not be too.

---

### Post by buzzingrobot on 2014-04-14
Gotta ask:  Why do you want to put up a page on a public web site to click on something that unlocks your house? 

Why not wait until you get home?

---

### Post by bashiergui on 2014-04-14
*sigh*

It is supposed to be the [Internet of Things]("http://en.m.wikipedia.org/wiki/Internet_of_Things") after all, I suspect we should all just suck it up and deal with it ;)

That being said, please understand in great depths all things about ssh or web portals or whatever you use to interface with your garage door. The fastest route to failure is to go with the defaults and not understand how it really works. Because I guarantee eventually someone malicious will find it that understands it very well.

Think about the best case and the worst case. I guess best case is your wife is locked out, you can let her in remotely and save the day. Worst case is you're on vacation and a script kiddie brute forces your password and manages to open the door. It sits open for days until you return to a house with no furniture inhabited by two families of raccoons and a rabid squirrel. If the risk is worth it then go for it.

---

### Post by pqwoerituytrueiwoq on 2014-04-14
why not run the script to open the door via ssh?
you could simple use a desktop launcher that runs a script via ssh using your ssh key
just throw this in a launcher
```
ssh [EMAIL="pi@raspberrypi.local"]pi@raspberrypi.local[/EMAIL] "/path/to/script.py"
```
i think you will need to be root to operate the GIOP, so keep that in mind

---

### Post by wlraider70 on 2014-04-14
I appreciate the security concerns. So lets say the website is internal only no forwarded ports yada yada. 
I'd still like to know if I can have the equivalent of an public key security on a website. 

I thought about a script via ssh, but this is incomprehensible for my wife.

---

### Post by pqwoerituytrueiwoq on 2014-04-15
that is why you give her a desktop launcher (as in a icon on her desktop) to call the script
if it is using only your wifi and you have WPA-ASE encryption a basic page will be safe, assuming www-data has permission to run the script to open the door

---

### Post by CharlesA on 2014-04-15
> **pqwoerituytrueiwoq said:**
> that is why you give her a desktop launcher (as in a icon on her desktop) to call the script
if it is using only your wifi and you have WPA-ASE encryption a basic page will be safe, assuming www-data has permission to run the script to open the door

It would be better to just use a passphrase less ssh key and an unprivlaged user set to run the script on login.

---

### Post by 1clue on 2014-04-15
OK just as a security observation, I just messed with a garage door opener remote not too long ago.  It had 10 3-position switches to set the combination.  So 3^10 is 59049 combinations.  I understand a standard door key (or car key) has about 10,000 combinations.

So let's say you have a bigger exposure because your device is on the Internet.  Even so, I think ssh with a required key would be more than enough here, as long as you have a secure box.

My concern is that an rpi might not have that much of a security audit.  But even so, I think you're probably not overly exposed, certainly there are other people doing the IoT thing and have had few problems if any.

With a web page you'd want it encrypted (https) which means a certificate of some sort, otherwise anyone with a wifi sniffer could see your password and it would be busted no matter how good your password is.  You could use a self-signed cert, but you'd need something.

IMO for this sort of thing, the ssh idea sounds easier and inherently safer.

---

### Post by CharlesA on 2014-04-15
> **1clue said:**
> OK just as a security observation, I just messed with a garage door opener remote not too long ago.  It had 10 3-position switches to set the combination.  So 3^10 is 59049 combinations.  I understand a standard door key (or car key) has about 10,000 combinations.

So let's say you have a bigger exposure because your device is on the Internet.  Even so, I think ssh with a required key would be more than enough here, as long as you have a secure box.

My concern is that an rpi might not have that much of a security audit.  But even so, I think you're probably not overly exposed, certainly there are other people doing the IoT thing and have had few problems if any.

With a web page you'd want it encrypted (https) which means a certificate of some sort, otherwise anyone with a wifi sniffer could see your password and it would be busted no matter how good your password is.  You could use a self-signed cert, but you'd need something.

IMO for this sort of thing, the ssh idea sounds easier and inherently safer.

I know the ssh thing was my idea, but you covered the most important points. :)

---

### Post by ant2ne on 2014-04-16
If your pi was connecting to the wifi network and you were using WPA2 with strong passwords then anyone "sniffing" would only see encrypted traffic between your device and the WAP. I'm trying to recall (it has been awhile) but I'm pretty sure that each connection to a WPA2 device has its own encryption certificate so even others connected to the WPA2 WAP with a valid log on password/key could not see another's traffic. If you planed to control the pi from within your own WIFI network then you'd not need https.

If you wanted your pi on the internet though using NAT/PAT so that you can access the pi from any internet connection in the world then you'd need to use https. You can use a self signed cert on the pi. Then just tell your laptop (other internet connected device) to import and keep that certificate. (You'd have to google up the steps) then that laptop would just trust that certificate. Or, the professional way (more expensive) would be to get a trusted 3rd party certificate like go daddy. There was theses guys (I cant recall the name.) that gives out free 3rd party certs for home users.

---

### Post by 1clue on 2014-04-16
Considering that the OP is using this for personal home security, a third party certificate is less than desirable.  The only people who SHOULD trust the cert are people in that family or 'circle of trust'.

If the pi can't handle the ssl cert, you could have a main Linux node with apache2 and a self-signed cert exposed to the Internet, and then use wired or WPA2 to the pi.  Use name-based virtual hosts on the exposed apache, and redirect to the proper device.  For example, [https://garage.myhouse.com](https://garage.myhouse.com) or [https://stereo.myhouse.com](https://stereo.myhouse.com), or my favorite, [https://foghornInMyDaughtersRoom.myhouse.com](https://foghornInMyDaughtersRoom.myhouse.com).  Or maybe electricCat.myhouse.com. :)

The rpi is so versatile, don't you think?

---

### Post by ant2ne on 2014-04-16
By 3rd party I mean like a world recognized cert from a Trusted Authority. For example, you trust godaddy's cert, and godaddy issues your server a cert. So your laptop gets a cert from your server, then knows godaddy issued it so it checks with godaddy who it trust to verify that the cert you got from your server is good.

---

### Post by 1clue on 2014-04-16
Exactly.  He's making a web page that he will use to open his garage door.  In what scenario would a third-party certificate be even desirable?  How many people are going to be involved here?  Certainly he doesn't want just anyone to do it.

If you're going to do this with a web server, then a self-signed cert is all you want.

---

### Post by ant2ne on 2014-04-16
Not thinking you know what a 3rd party cert is. So, you know when you goto a website and it says something about the certificate not trusted and asks if you want to continue? A valid 3rd party solves that problem. It is just (if not more) secure than a self signed. It will provide confidentiality during the log on and execution process of the pi's web application.

---

### Post by CharlesA on 2014-04-16
Why bother with dealing with ssl certs and stuff when you can just run a script/command via ssh and be done with it..

---

### Post by SeijiSensei on 2014-04-16
> **CharlesA said:**
> Why bother with dealing with ssl certs and stuff when you can just run a script/command via ssh and be done with it..

Because many people prefer GUI interfaces with nice shiny buttons to press?

I haven't given this problem a whole lot of thought, but I'd probably set up a web page using PHP and a self-signed certificate to encrypt the login process.  Have the PHP script run the appropriate command using shell_exec() if the person authenticates correctly.  If you don't want to build authentication into the application itself, which is surely overkill in this case, just use [Apache basic authentication]("http://httpd.apache.org/docs/2.2/howto/auth.html") with an HTTPS connection.

---

### Post by 1clue on 2014-04-16
> **ant2ne said:**
> Not thinking you know what a 3rd party cert is. So, you know when you goto a website and it says something about the certificate not trusted and asks if you want to continue? A valid 3rd party solves that problem. It is just (if not more) secure than a self signed. It will provide confidentiality during the log on and execution process of the pi's web application.

I run several PCI compliant servers.  I've been buying SSL certificates for more than a decade.  A third party certificate adds expense and, in this case, gets absolutely nothing of value in return.  The only difference between a third party cert and a self-signed cert is that the third party can cost more than a thousand dollars per year, and the self-signed is free.  The automatic browser recognition of a 'valid' certificate is worth exactly this:  You don't have to look at the "unknown certificate" window the first time you load the page.

In the case you're going to some sort of site that processes credit cards, or maybe a bank site, you get a lot from a third party certificate.  It lets people who don't know the owner of the web site that the certificate authority (verisign, thawte, etc) has taken certain measures to verify that the web site is being run by a valid business and has a legal identity.  In my experience, the more expensive the certificate the more painful the interview process is, and the higher the 'quality' of the endorsement is.  For example, Verisign charges up to USD $1750 per year for their standard certificates, and their validation is extremely inconvenient for the people buying the certificate.  Thawte, although owned by the same company, has less stringent requirements and a less painful interview process.

Frankly I think that for either of these certificate authorities, I don't think they would issue a certificate for some guy's garage door for any price.  The price of the certificate has nothing to do with the quality of the encryption key, because they never actually have the key.  You generate it, you make a CSR and you send that in.  The private key never crosses the network.

---

### Post by 1clue on 2014-04-16
> **CharlesA said:**
> Why bother with dealing with ssl certs and stuff when you can just run a script/command via ssh and be done with it..

+1.

As much as I've dealt with web site certificates in the past, it's still way too much of a pain to set up a web site.  I'd make an android app on my smart phone hooked to the ssh script.

---

### Post by CharlesA on 2014-04-16
> **SeijiSensei said:**
> Because many people prefer GUI interfaces with nice shiny buttons to press?

I haven't given this problem a whole lot of thought, but I'd probably set up a web page using PHP and a self-signed certificate to encrypt the login process.  Have the PHP script run the appropriate command using shell_exec() if the person authenticates correctly.  If you don't want to build authentication into the application itself, which is surely overkill in this case, just use [Apache basic authentication]("http://httpd.apache.org/docs/2.2/howto/auth.html") with an HTTPS connection.

True, but couldn't it just have an icon pointing to the script and just work when doubled clicked?

---

### Post by SeijiSensei on 2014-04-17
> **CharlesA said:**
> True, but couldn't it just have an icon pointing to the script and just work when doubled clicked?

I presume we're talking about an application that can be activated from a cell phone.  Writing an app for Android or iOS isn't as simple as writing a web app that can be run from a browser on the phone.

If the application was designed for a regular PC, I'd agree your solution is preferable.

---

### Post by CharlesA on 2014-04-17
> **SeijiSensei said:**
> I presume we're talking about an application that can be activated from a cell phone.  Writing an app for Android or iOS isn't as simple as writing a web app that can be run from a browser on the phone.

If the application was designed for a regular PC, I'd agree your solution is preferable.

Good point. I was thinking of using something like JuiceSSH or ConnectBot, but I'm not sure if either of those allow scripting or macros or whatever.

Thanks!

---

### Post by 1clue on 2014-04-17
There are android ssh clients, surely there's some sort of button that lets you script something with ssh.

---

### Post by SeijiSensei on 2014-04-17
I use JuiceSSH; it has no such ability even in its premium version.  Perhaps one of the other clients do.

You can apparently customize the command that Juice uses to connect. It appears to use a program called "[mosh-server]("http://mosh.mit.edu/")."  I don't know whether it's customizable in the way you describe, though, and there are no man pages accessible from the terminal in Android.  In fact there isn't a "man" program at all.  

I'm running Android 4.3 on a Galaxy S3.

---

### Post by CharlesA on 2014-04-17
If that's the case, then it would probably have to be a web app then, even if it's a simple "go to this page and click on "open/close."

---

