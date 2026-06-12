---
title: "HOW: applying TOR system-wide"
date: 2012-04-02
forum: Security
---

### Post by AbuAkram on 2012-04-02
Hi, this is my first post on this forum... definetly not the last      ):P

I'm living in the Sudan which is blocked by some countries so I can't use their repositories... for example I can't install Maemo 5 SDK cause it's nokia repository has blocked Sudan.

Now, I have tried to get my ubuntu 11.10 use TOR system-wide. Also installed Vidalia and Privoxy

But didn't manage to use apt-get through TOR

Checked many sites but none really helped

Has anyone successfully managed running his device through TOR system-wide? Then please tell me how

:)

---

### Post by AbuAkram on 2012-04-03
Karam at talk.maemo.org has a solution how to route the whole device through tor... 

[http://talk.maemo.org/showthread.php?t=81673](http://talk.maemo.org/showthread.php?t=81673)

what he did is (after installing tor on his N900 running maemo 5) he added some lines into /etc/apt/apt.conf.d/00maemo

the original 00maemo files looks like this:

> Acquire::Queue-Mode "access";
Acquire::https::Verify-Peer "false";
APT::Install-Recommends 0;

and he added some lines and it looks now like this:

> Acquire::Queue-Mode "access";
Acquire::https::Verify-Peer "false";
APT::Install-Recommends 0;


Acquire {
Retries "0";
HTTP {
Proxy "http://127.0.0.1:8118";
};
};

now I can easily use apt-get on my N900 which runs now through Tor

CAN THIS BE APPLIED ON UBUNTU 11.10?

WHICH FILE HAS TO BE MODIFIED & AND HOW?

---

### Post by ottosykora on 2012-04-03
forget privoxy etc, go to the torproject.org, obtain latest version of to r from there and latest version of torbutton for firefox from there and off you go.

It is possible to use to now via SOCKS, but it does not work allways well, but the http/https way it works fine.

Still better solution: get the bundled browser from torproject.org and use this. Lot of modifications are done to it so your original ip can not be disclosed.

---

### Post by haqking on 2012-04-03
> **ottosykora said:**
> forget privoxy etc, go to the torproject.org, obtain latest version of to r from there and latest version of torbutton for firefox from there and off you go.

It is possible to use to now via SOCKS, but it does not work allways well, but the http/https way it works fine.

Still better solution: get the bundled browser from torproject.org and use this. Lot of modifications are done to it so your original ip can not be disclosed.

how will the OP do apt-get through a browser ;-)

---

### Post by AbuAkram on 2012-04-03
> **haqking said:**
> how will the OP do apt-get through a browser ;-)

exatly, that's the point

---

### Post by haqking on 2012-04-03
> **AbuAkram said:**
> exatly, that's the point

I dont use ubuntu anymore but this works well

[http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/](http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/)

it uses polipo instead of privoxy and works great.

I use tor and polipo on my debian build and slackware build and use the socks proxy for IRC, i used to use it system wide now only for IRC though.

Hope this helps

---

### Post by DanR01 on 2012-04-03
What about downloading proxychains from the Sourceforge site?

I'm pretty sure you can add a line in the config file to force connections though Tor.

Then you can prefix commands with proxychains to route through the Tor network

E.g. proxychains elinks cmyip.com

Not tried it with apt-get though.

Dan

---

### Post by AbuAkram on 2012-04-03
> **haqking said:**
> I dont use ubuntu anymore but this works well

[http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/](http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/)

it uses polipo instead of privoxy and works great.

I use tor and polipo on my debian build and slackware build and use the socks proxy for IRC, i used to use it system wide now only for IRC though.

Hope this helps

It sounded very promising, I went through the steps provided, downloaded the config file and replaced it with the original one in /etc/polipo/config... restarted tor & polipo changed the network settings to http/https: 127.0.0.1:8118 and socks to 127.0.0.1:9050 and applied system-wide...

opened terminal and checked it out with "curl config.me" but got to see my real ip......

NOT WORKING

I also checked this page out
[http://www.webupd8.org/2009/09/how-to-install-tor-in-ubuntu-debian.html](http://www.webupd8.org/2009/09/how-to-install-tor-in-ubuntu-debian.html)

instead of polipo he used privoxy... it is said that polipo is faster while privoxy is safer...

anyhow, didn't work too

I only succeed to hide my ip while browsing but not system-wide..........

Where is teh TRICK?

---

### Post by ottosykora on 2012-04-04
> **haqking said:**
> how will the OP do apt-get through a browser ;-)

ok missed that, in such case it has to be configured to work via SOCKS

---

### Post by ottosykora on 2012-04-04
just to remind:

the current version of tor does not use any polipo or privoxy etc.
It works on it own, it uses its own build in kind of proxy for html traffic and it can be set up to use socks5 to divert all traffic.

check torproject.org for details

---

### Post by ottosykora on 2012-04-04
> socks to 127.0.0.1:9050  <

use port 9051

---

### Post by AbuAkram on 2012-04-04
> **ottosykora said:**
> > socks to 127.0.0.1:9050  <

use port 9051

I did and that's the result:

> $ curl ipconfig.me
<html>
<head>
<title>Tor is not an HTTP Proxy</title>
</head>
<body>
<h1>Tor is not an HTTP Proxy</h1>
<p>
It appears you have configured your web browser to use Tor as an HTTP proxy.
This is not correct: Tor is a SOCKS proxy, not an HTTP proxy.
Please configure your client accordingly.
</p>
<p>
See <a href="https://www.torproject.org/documentation.html">https://www.torproject.org/documentation.html</a> for more information.
<!-- Plus this comment, to make the body response more than 512 bytes, so      IE will be willing to display it. Comment comment comment comment      comment comment comment comment comment comment comment comment.-->
</p>
</body>
</html>
so what you say is that polipo can be removed? right? Only TOR is needed (and VIDALIA to redirect the browser)...

I removed PRIVOXY and did TOR restart and when doing "curl ipconfig.me" I get ""curl: (7) couldn't connect to host""

I mean, when looking at my 1st post I mentioned a possibility on the N900 device using Maemo 5... In ubuntu only a file in "/etc/apt/apt.conf.d/"... right? I just don't know which and how??

CORRECTION: check out: gedit /etc/apt/apt.conf

---

### Post by haqking on 2012-04-04
> **AbuAkram said:**
> 

CORRECTION: check out: gedit /etc/apt/apt.conf

Yes you will need to edit that to reflect your network configuration

---

### Post by AbuAkram on 2012-04-04
> **haqking said:**
> Yes you will need to edit that to reflect your network configuration

HOW?  What has to be added?

---

### Post by haqking on 2012-04-04
> **AbuAkram said:**
> HOW?  What has to be added?

something along the lines of (edit to suit)

```
Acquire::http::proxy "http://proxy.com:<port>/";
```

so probably

```
Acquire::http::proxy "127.0.0.1:9050/";
```


You will need to check syntax on that its been a while and i never had any apt issues with tor.

You may need to add ftp and https entries also

Like i said you best double check this as i cant check it right now

---

### Post by ottosykora on 2012-04-04
>so what you say is that polipo can be removed? right? Only TOR is needed (and VIDALIA to redirect the browser)...

I removed PRIVOXY and did TOR restart and when doing "curl ipconfig.me" I get ""curl: (7) couldn't connect to host""<


if you use the current version from torproject.org, you only install tor and nothing else so far. Polipo and Privoxy is not needed this way, thought it still might be used.

Hmm, vidalia, well this is other matter, you will not be able to use vidalia straight away as you may have used it before. In fact the current tor does not need the vidalia too.
To use vidalia, you need to stop tor first and then you could start it again from vidalia.
The tor is now default configured to run at start up after you install it.


Q: what version of tor do you use? 2.2.23 ? Or other?

---

### Post by AbuAkram on 2012-04-04
> Q: what version of tor do you use? 2.2.23 ? Or other?

v0.2.2.35

---

### Post by haqking on 2012-04-04
> **AbuAkram said:**
> v0.2.2.35

I think if you stick with existing or initial config and just edit your apt.conf to configure proxy settings you will be good.

Cheers

---

### Post by AbuAkram on 2012-04-04
> I think if you stick with existing or initial config and just edit your apt.conf to configure proxy settings you will be good.

I fully agree, the point is, I don't know how :sad:

---

### Post by AbuAkram on 2012-04-04
I tried messing around with

/etc/apt/apt.conf
/etc/tor/torrc
/etc/tor/tor-tsocks.conf

and many more....

and then checked out in terminal "curl ipconf.me" and always my real IP was shown... 

just can't succeed that terminal accesses the internet through tor

---

### Post by ottosykora on 2012-04-05
the current versions of tor are indeed kind of confusing, as all behaves quite differently as before.

The torproject guys just say tha we have to torify programs ourselves, all they seem to care about is the firefox browser.

however, to use apt-get you in fact are not after torifying the terminal but aptitude itself.

Somewhere I read :

sudo torify apt-get install mc

Try that

The setup seems to be rather automatic today, all ports set to 'auto', tor is in fact running all the time unless you go and stop it, so even vidali will give errors when trying to run it.

They simply seem to say , if the program uses socks5, nice it may work, if not, help yourselves.

---

I just tried following:
make sure tor operates at somehow, I tested with firefox and the torbutton pugin, it confirmed on the test site that I am using tor.

Then did sudo torify apt-get update

it checks different connections but seems to do the job.

But I am not 100% sure how this works as for me in my location all gets in and out.

Pls try

----

just tried

curl ifconfig.me

returns my actaul public address


torify curl ifconfig.me

returns the address which it looks like when using tor
(same as shown in the browser on the tor check page)

so the torify command seems to work this way.

---

### Post by AbuAkram on 2012-04-05
IT WORKED

but now a new problem has approached

the thing is I am trying to install Maemo 5 SDK in a scratchbox, but nokia's repository has blocked my country's IP... 

torify command works well but not in scratchbox

this is what I get:

[sbox-FREMANTLE_X86: ~] > torify apt-get update
bash: torify: command not found

hmmmmmmm

---

### Post by ottosykora on 2012-04-05
oh, slowly I am not sure how further.

The tor folks say torify each program separately.

To download something, you can use the browser with the torbutton.

Additional software needs to be 'torified ' separately. How not sure.

Oh yes, scrathbox, separate system, not using tor , is there away to include tor to the scrathcbox?


---
OK I had quick look at what this scratch box is about, here I assume it could be difficult alltogether. This is one thoise quemu thigs, which are neither a virtual machine nor just part of the give os.

It might be at the end more useful to have virtual machine, as virtual box. This can be installed from the ubuntu repos. 
I did so far not operate tor from an virtual machine, but it could work at the end. The virtual machine gets separate private address, but will get the same public address and tor running in it could well behave similar as in the host machine.

If you try and manage, let us know here if worked.

---

### Post by AbuAkram on 2012-04-05
>  scrathbox, separate system, not using tor , is there away to include tor to the scrathcbox?

Thanks Ottosykora for your concern

There are some questions to be answered that helps to move forward with success

Tor routes through socks at port 9050, right?

And on ubuntu 11.10 under System Settings --> Network --> Network Proxy one can manually define how ubuntu connects to the outer world...

Now, even if, you give in values used by tor and apply that system wide, it seems that it has no effect on how ubuntu connects to the outer world. It only affects the browser but doesn't affect anything else...

It should, since it says system wide, including scratchbox, since it's door to the outer world is routed to the socks used by tor...

Am I right here? or am I missing something............

---

### Post by ottosykora on 2012-04-05
>Tor routes through socks at port 9050, right?<
yes this is default for socks5

>And on ubuntu 11.10 under System Settings --> Network --> Network Proxy one can manually define how ubuntu connects to the outer world...<

hmmm, but that tor needs also thigs like control port, this can be different, but is often 9051 when used with http.

>Now, even if, you give in values used by tor and apply that system wide, it seems that it has no effect on how ubuntu connects to the outer world. It only affects the browser but doesn't affect anything else...<

this is quite right, as tor people seem to be very reluctant to use tor system for systemwide operation. I do not know just now if they did something to the current version that makes the systemwide use so difficult.

You may check in the browser, how it looks like when you connect it with the aid of the torbutton.

In fact however, the configuration files of the tor are in the current version more less doing nothing, as all is set there to 'automatic'.

But if you tell the network to use 9050 as proxy, it should do.

But! I have doubt that zthigs like scratchbox will be able to use it.
Such thigngs, which are kind of half virtual machine use often some extra network and therefore may well bypass the tor on the host.

If you run virtual machine on the host, it will also bypass the proxy set for the host as it will use its own networking.

Therefore I have some doubts about scratchbox being able to use the tor proxy of the host too.

The port 9050 will be used if set for proxy, as socks5 port, also if programs are not configured or able to use socks5 directly, then they may also bypass the tor this way.

I think this is all the kind of problems torproject people are fighting and as there are so many ways to bypass the tor, they strongly do not recommend to make tor systemwide.

Well if you set the proxy in the notwork, then go to terminal and call the ifconf.me without the 'torify', do you get the real or pretended address?
( I can not test now, have no proper machine to hand now)


It should, since it says system wide, including scratchbox, since it's door to the outer world is routed to the socks used by tor...

---

### Post by AbuAkram on 2012-04-06
> You may check in the browser, how it looks like when you connect it with the aid of the torbutton.
I have tor installed without polipo, tor button or privoxy. I defined under Network settings http/https/ftp: 127.0.0.1:8118 & socks:127.0.0.1:9050 and applied it System-Wide.
Defined in my browser socks5: 127.0.0.1:9050 and left http/https/ftp blank. And when checking with check.torproject.org "I have tor installed" PERFECT.
I have to mention that http/https/ftp has to be kept blank or it will fail to conect to tor. 

> Well if you set the proxy in the notwork, then go to terminal and call the ifconf.me without the 'torify', do you get the real or pretended address?
No it doesn't work... I have to torify it to work or else I get this:

> <html>
<head>
<title>Tor is not an HTTP Proxy</title>
</head>
<body>
<h1>Tor is not an HTTP Proxy</h1>
<p>
It appears you have configured your web browser to use Tor as an HTTP proxy.
This is not correct: Tor is a SOCKS proxy, not an HTTP proxy.
Please configure your client accordingly.
</p>
<p>
See <a  href="https://www.torproject.org/documentation.html">https://www.torproject.org/documentation.html</a>  for more information.
<!-- Plus this comment, to make the body response more than 512  bytes, so      IE will be willing to display it. Comment comment comment  comment      comment comment comment comment comment comment comment  comment.-->
</p>
</body>
</html>


What is the point of having System-Wide option if it is of no use???

You have checked my very first post with the solution for N900 device using Maemo5?

Is that a different TOR? Or has Maemo 5 a different policy?

Guess I have to establish a net connection through TOR with my N900 and use that with my ubuntu through Hotspot or something to get my task done......

---

### Post by ottosykora on 2012-04-06
what I was told at least, is that not all programs are able to use socks5 directly and this is the point where torproject people say the systemwide is not systemwide and should be used with big care if used for secure hiding of your identity.

The systemwide idea is ok, but we have to uderstand that if it is possible for programs to create own virtual network adapter and bypass the given settings also we may expect that programs will not participate on using proxy.
After all we do not deal with any physical devices here, just programs passing data to each other.

I am not sure about the message you get about tor and http proxy.
In fact the http proxy function was standard for long time, until the recent versions.
But at the moment now not sure why it thinks it is not configured for socks5 and just for http.

On my system, I have the tor switched off, starting it manually on demand, as only then configuration changes are possible. And I use only specific programs to use tor,  so I never get any message like you did.
I just thought the port 8118 is not needed for the current versions if 9050 is used for socks5.
However, the programs have to be able to use socks5 then.

---

### Post by haqking on 2012-04-06
I am confused, you said it works.

So you had Tor working ?

so all you needed to do was edit your apt.conf file ?

Did you do this or did it not work ?

---

### Post by ottosykora on 2012-04-07
@abuakram

you are making me to read all this endless stuff on the torproject site! So far I never did that really, as it is lot to read, but your thread here is forcing me to do something for my education.

The things seem to be more complex then I thought.

However, I found few things, still not understanding all, but for local redirect, they recommend to insert following to the torcc:

AutomapHostsOnResolve 1
TransPort 9040
DNSPort 53


however I think for the time being the line with the dns could be temporary commented out.

---

### Post by AbuAkram on 2012-04-07
> you are making me to read all this endless stuff on the torproject site! So far I never did that really, as it is lot to read, but your thread here is forcing me to do something for my education.

I really appreciate that... thanks alot... people like you are very rare  

@Haqking: Sorry I didn't reply since your post, our Network Provider crashed down.... Anyhow it's back and I am trying something out including @ottosykora's advice and inform you..... perhaps tonight

):P

---

### Post by ottosykora on 2012-04-07
In fact the more I did read this night, the more confused I became.

The howtos for system wide tor use in fact are set up with the port 9040 (??) but furthermore they want us to capture and redirect the traffic by the use of IP tables.

I remember that I was always told, use tor for surfing and download, or better say all which goes in your browser, do not use it for other things.

I will try to read that stuff again, but it seems even when installing one of those proxies, the things will not do what expected this way. 

Privoxy might be able to sort out different protocols, polipo is more supposed to be used for http.



To have a complete and transparent connection it looks like some of those vpn services would be the best.

---

### Post by haqking on 2012-04-07
> **ottosykora said:**
> In fact the more I did read this night, the more confused I became.

The howtos for system wide tor use in fact are set up with the port 9040 (??) but furthermore they want us to capture and redirect the traffic by the use of IP tables.

I remember that I was always told, use tor for surfing and download, or better say all which goes in your browser, do not use it for other things.

I will try to read that stuff again, but it seems even when installing one of those proxies, the things will not do what expected this way. 

Privoxy might be able to sort out different protocols, polipo is more supposed to be used for http.



To have a complete and transparent connection it looks like some of those vpn services would be the best.

I dont know why its so complicated or if things have changed.

I have tor with polipo and it works system wide.

I only use it for IRC these days but if i choose system wide then it just works including apt in debian.

It works the same in slackware too.

---

### Post by ottosykora on 2012-04-07
> **haqking said:**
> I dont know why its so complicated or if things have changed.

I have tor with polipo and it works system wide.

I only use it for IRC these days but if i choose system wide then it just works including apt in debian.

It works the same in slackware too.

According to the tor site, it does not work systemwide, each program has to be torified separately, that means pointed to the proxy.
As far as I understood all those texts, the tor people used those proxy programs beacuse of some bug in the firefox, but his was fixed by mozilla with version 3, so from there on they do not use polipo any more, thought one can install it, but it does apparently lead to nice http proxy, but not more.

But I am just in progress of trying to do what I was supposed to do long time ago, namely read all this stuff so I can understand a fraction of it.

---

### Post by ottosykora on 2012-04-07
Trying to understand:
[https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy#LocalRedirectionThroughTor](https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy#LocalRedirectionThroughTor)

tor guys have apparently problem with DNS and therefore the complexity.

---

### Post by haqking on 2012-04-07
> **ottosykora said:**
> According to the tor site, it does not work systemwide, each program has to be torified separately, that means pointed to the proxy.
As far as I understood all those texts, the tor people used those proxy programs beacuse of some bug in the firefox, but his was fixed by mozilla with version 3, so from there on they do not use polipo any more, thought one can install it, but it does apparently lead to nice http proxy, but not more.

But I am just in progress of trying to do what I was supposed to do long time ago, namely read all this stuff so I can understand a fraction of it.

well it works for me, i dont use firefox.

Tor and polipo was a simple install.  Yes you still have to configure some programs even if system wide is enabled.

But all works for me.

Peace

---

### Post by ottosykora on 2012-04-07
so far tor seems to currently support directly only firefox browsing.

The Q for you is there how did you manage to install it system wide. System wide would mean, that also programs which simply do not have any possibility to be routed to a local proxy would be able to use it.

Did you make the filtering with the IP tables?

---

### Post by AbuAkram on 2012-04-08
I guess it depends on what distro one uses. Ubuntu doesn't, that's for sure, in debian and slackware it does, as @Haqking mentions. It does work too under Maemo 5 which is based on Linux.

@haqking: can you tell me please how you configured tor to function system wide an what Distro you are using?

---

### Post by haqking on 2012-04-08
> **AbuAkram said:**
> I guess it depends on what distro one uses. Ubuntu doesn't, that's for sure, in debian and slackware it does, as @Haqking mentions. It does work too under Maemo 5 which is based on Linux.

@haqking: can you tell me please how you configured tor to function system wide an what Distro you are using?

well when i said system wide i meant by enabling the proxy in global network settings which then applies to most network activity.

As i said above i still had to enable it for certain applications.

I use it in debian for IRC only, in slackware for IRC only, and used to use it in Ubuntu for browsing and IRC and IM.

I now run mainly slackware and use it only for IRC and i have Tor with Polipo.

I dont live in a country where my IP is blocked for alot of services though, though if it was and i was you i would edit the apt.conf file which you still have not mentioned the result of.

Peace

---

### Post by AbuAkram on 2012-04-08
> i would edit the apt.conf file which you still have not mentioned the result of.

I tried every possible solution, didn't work for me......... 

Do you know a possibility to edit the file?

---

### Post by haqking on 2012-04-08
> **AbuAkram said:**
> I tried every possible solution, didn't work for me......... 

Do you know a possibility to edit the file?

well i dont know what you did and didnt do.

did you follow my [post #15 above]("http://ubuntuforums.org/showpost.php?p=11816681&postcount=15")

---

### Post by AbuAkram on 2012-04-08
> **haqking said:**
> well i dont know what you did and didnt do.

did you follow my [post #15 above]("http://ubuntuforums.org/showpost.php?p=11816681&postcount=15")

Yes I did, tried:

1-
Acquire::http::proxy "127.0.0.1:9050/";
and tried

2-
Acquire::http::proxy "127.0.0.1:8118/";
Acquire::https::proxy "127.0.0.1:8118/";
Acquire::ftp::proxy "127.0.0.1:8118/"; 
Acquire::socks::proxy "127.0.0.1:9050/"; 

and tried

3-
Acquire::socks::proxy "127.0.0.1:9050/"; 

None does what it should

---

### Post by Paddy Landau on 2012-04-08
Reading this thread made me wonder if you could use a much simpler technique.

Tor + Privoxy are for anonimity. You don't actually need anonymity. You just need to show yourself as being in an "approved" country.

For that, all you need is a proxy. Nothing more. (Tor will slow you down unnecessarily as well as slowing down other Tor users.)

So, how about searching for free proxy servers (many are available) -- or, if you have the money, use a paid-for service for faster access.

Once you have a proxy address, you should find it easy to add to your network manager, and you're done.

I have only once used this (at my ISP's request when they had a temporary problem), and it is easy as can be.

I think it's worth a try in your case.

**EDIT**: BTW, to prevent smileys appearing in the code that you paste, surround the code with [noparse]```
[/noparse] and [noparse]
```[/noparse].

---

### Post by haqking on 2012-04-08
> **Paddy Landau said:**
> Reading this thread made me wonder if you could use a much simpler technique.

Tor + Privoxy are for anonimity. You don't actually need anonymity. You just need to show yourself as being in an "approved" country.

For that, all you need is a proxy. Nothing more. (Tor will slow you down unnecessarily as well as slowing down other Tor users.)

So, how about searching for free proxy servers (many are available) -- or, if you have the money, use a paid-for service for faster access.

Once you have a proxy address, you should find it easy to add to your network manager, and you're done.

I have only once used this (at my ISP's request when they had a temporary problem), and it is easy as can be.

I think it's worth a try in your case.

+1

I was just assuming the OP wanted to specifically use Tor.

but yes you could forego TOR altogether and use a proxy.

or a secure VPN of which there are many.

---

### Post by ottosykora on 2012-04-08
I am sometimes using some proxies too, but also here I met many of those free services being http proxy only, so nice for surfing or http downloading, but not properly handling the rest.

The Tor itself is also not everything, it seems not to handle any UDP things at all for example. 

Many things may work apparently with Tor, but the torproject people figured out that there are DNS requests sent where not wanted. 

But if traffic is captured filtered by IP tables and fed to the Tor, then all will be forwarded, but not all protocols will leave the exit nodes. There are some protocols blocked there too.

A full transparent vpn service might be the right thing really, letting all traffic through without any restrictions.

---

### Post by AbuAkram on 2012-04-09
So I guess this is it........ thanks alot to all for your help... 

If I come up with anything new, I'll gladly post it....

---

### Post by Paddy Landau on 2012-04-09
> **AbuAkram said:**
> So I guess this is it...
What did you decide to do?

---

### Post by AbuAkram on 2012-04-09
> What did you decide to do?

Since editing 00maemo file in /etc/apt under Maemo 5 works perfectly, I am going to try it under different distros... ofcourse youre right, VPN or proxies are possibilties I am going to use, but I guess that it should work with tor too some way some how....

---

### Post by Paddy Landau on 2012-04-10
Good, I'm glad it's working now.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by AbuAkram on 2012-04-10
> Good, I'm glad it's working now.

No, it's not working under Ubuntu... that was the matter from the beginning.

It works under Maemo 5, but not under Ubuntu.

SOLVED under different other distro, NOT SOLVED under Ubuntu.

---

### Post by Paddy Landau on 2012-04-10
Oh, I see, sorry.

If you try the free proxy method, let us know what happens.

---

### Post by ottosykora on 2012-04-11
@abuakram

did you try the method described by torproject?

[https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy#LocalRedirectionThroughTor](https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy#LocalRedirectionThroughTor)

---

### Post by AbuAkram on 2012-04-12
@Ottosykora: I will try it out as soon as possible and let you know the results... didn't have much time lately...was sort of busy.....

Until then: could I have some informations about these files and their functions:

1- /etc/resolv.conf
2- /etc/apt/apt.conf

what are thier functions? and difference between both?

Thanks in advance

---

### Post by haqking on 2012-04-12
> **AbuAkram said:**
> @Ottosykora: I will try it out as soon as possible and let you know the results... didn't have much time lately...was sort of busy.....

Until then: could I have some informations about these files and their functions:

1- /etc/resolv.conf
2- /etc/apt/apt.conf

what are thier functions? and difference between both?

Thanks in advance

resolv.conf is for dns

apt.conf is the configuration file for aptitude (apt)

neither are related

and apt.conf is the one you were editing earlier right ?

Peace

---

