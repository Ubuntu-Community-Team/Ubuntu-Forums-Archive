---
title: "Ubuntu 10.04 and Tor"
date: 2010-05-04
forum: Security
---

### Post by Richiegs on 2010-05-04
I just upgraded to Ubuntu 10.04, but I could not find any instructions on how to install Tor for Ubuntu 10.04. Any suggestions? Thanks

---

### Post by 2061.shy on 2010-05-05
Hi,
I think guides like
[http://www.webupd8.org/2009/09/how-to-install-tor-in-ubuntu-debian.html](http://www.webupd8.org/2009/09/how-to-install-tor-in-ubuntu-debian.html)
would work for any version.

---

### Post by rookcifer on 2010-05-05
> **Richiegs said:**
> I just upgraded to Ubuntu 10.04, but I could not find any instructions on how to install Tor for Ubuntu 10.04. Any suggestions? Thanks

First open a terminal and cut and paste this command:

```
sudo echo 'deb http://deb.torproject.org/torproject.org lucid main' > /etc/apt/sources.list.d/tor.list && gpg --keyserver keys.gnupg.net --recv 886DDD89 && gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - && sudo aptitude update && sudo aptitude install tor tor-geoipdb polipo
```

The above installs the official Tor project repo and adds their key.

Now edit the polipo config file like so:

```
sudo gedit /etc/polipo/config
```

Now *delete everything* in that file and replace it with [this configuration]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf").  Be sure to hit "save" on gedit and then exit it.  This config file is directly from the official Tor website.

Now type this:

```
sudo service tor restart && sudo service polipo restart
```

Then in Firefox install the "torbutton" add-on.

You now have a fully functional Tor setup ready for action. :guitar:

---

### Post by Richiegs on 2010-05-07
[QUOTE=rookcifer;9241642]First open a terminal and cut and paste this command:

```
sudo echo 'deb http://deb.torproject.org/torproject.org lucid main' > /etc/apt/sources.list && gpg --keyserver keys.gnupg.net --recv 886DDD89 && gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - && sudo aptitude update && sudo aptitude install tor tor-geoipdb polipo
```The above installs the official Tor project repo and adds their key.

It did not work. Permission denied!

---

### Post by rookcifer on 2010-05-08
There should be no "permission denied" if you entered your sudo password.  Please post the exact output from the terminal after you run the command.  I am not sure what "permission denied" in this context is referring to.  I double checked the command and everything looks correct.

---

### Post by OpSecShellshock on 2010-05-08
Or was it "permission denied" from the website, as in the http response code?

---

### Post by carranty on 2010-05-09
I'm having the same issue.  I've just upgraded to 10.04 and would like to get Tor installed.  I tried the above command and got 


bash: /etc/apt/sources.list: Permission denied

as a response.

---

### Post by carranty on 2010-05-09
In fact it never even asked me for my sudo password, just gave the above output straight away.

---

### Post by perkins99 on 2010-05-10
Try this instead:

```
sudo echo 'deb http://deb.torproject.org/torproject.org lucid main' | sudo tee -a /etc/apt/sources.list && gpg --keyserver keys.gnupg.net --recv 886DDD89 && gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - && sudo aptitude update && sudo aptitude install tor tor-geoipdb polipo
```

[http://stackoverflow.com/questions/850730/how-can-i-append-text-to-etc-apt-sources-list-from-the-command-line](http://stackoverflow.com/questions/850730/how-can-i-append-text-to-etc-apt-sources-list-from-the-command-line)

> The [tee]("http://en.wikipedia.org/wiki/Tee%5F%28command%29") command is called as the superuser via *sudo*  and the *-a* argument tells tee to append to the file instead of  overwriting it.
  Your original command failed, as the IO redirection with *>>*  will be done as the regular user, only your echo was executed with  sudo.


---

### Post by impert on 2010-05-12
The instructions on the [Tor site]("http://http://www.torproject.org/docs/debian.html.en#ubuntu") worked well for  me. It's pretty much what Richiegs posted, but the commands are not strung together.
If all else fails you could always try sudo su. Sometimes there are things that sudo won't let you do for some reason.

@ carranty:
**sudo** /etc/apt/sources.list

If you forget to use sudo for commands which require root permissions, you can use sudo !! to repeat the last command. You will have to give your password, of course.

---

### Post by todd1049 on 2010-05-16
I tried the instructions on the tor web page ([http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)), but when I typed the command

$ gpg --keyserver keys.gnupg.net --recv 886DDD89

I got the following message:

gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

For those who were able to install it, how did you get around (or avoid) this problem?  I am able to load the keys.gnupg.net site in firefox, but when I do a search for key 886DDD89, the site tells me there is no such key.  I am using 10.04, and am wondering if that is causing a problem.

---

### Post by rookcifer on 2010-05-16
> **todd1049 said:**
> I tried the instructions on the tor web page ([http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)), but when I typed the command

$ gpg --keyserver keys.gnupg.net --recv 886DDD89

I got the following message:

gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

For those who were able to install it, how did you get around (or avoid) this problem?  I am able to load the keys.gnupg.net site in firefox, but when I do a search for key 886DDD89, the site tells me there is no such key.  I am using 10.04, and am wondering if that is causing a problem.

Try a different keyserver.  I often have problems with some of them (the Ubuntu keyserver is the worst).  Try this:

gpg --keyserver pgp.mit.edu --recv 886DDD89

---

### Post by todd1049 on 2010-05-21
Hi rookcifer, thanks for the tip, but the mit.edu site did not work, either.  The result was the same.  Can you recommend any other sites I could try?  Thanks.

---

### Post by crashus on 2010-06-01
yup I'm having the same problem.

Permission denied.

Didn't even asked me for the sudo password, so I tired first the sudo -s, than the command, and I got:
```
sudo echo 'deb http://deb.torproject.org/torproject.org lucid main' | sudo tee -a /etc/apt/sources.list && gpg --keyserver keys.gnupg.net --recv 886DDD89 && gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - && sudo aptitude update && sudo aptitude install tor tor-geoipdb polipo
deb http://deb.torproject.org/torproject.org lucid main
gpg: WARNING: unsafe ownership on configuration file `/home/uros/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

```

---

### Post by 1oki on 2010-06-02
I am having the same issue, and narrowed it down to the port being blocked by my firewall (port # 11371). I am here at work, and instead of going into my cisco to open it, I am just going to try to do an ssh tunnel and forward this port...

---

### Post by PDA1 on 2010-06-15
I got Vidalia running and it says I'm connected to the Tor network.  However, when I check if I'm *really* connected to Tor using some address at Tor that'll verify I'm on Tor...it says I'm not.  But, I can look at the Network map on Vidalia.

On the other hand.....if I shut down Vidalia and use the TorButton......then Tor says I'm indeed on Tor and have a different Ip address.

Any ideas?

---

### Post by GrandTheft on 2010-07-09
backup your sources.list before applying any command from this post.

Best regards, 
GT

---

### Post by sattahs on 2010-07-27
thank you all,  perkins and rookcifer. i am new to linux and i am  studying the pocket guide by Keir thomas. everything seems to be working fine as i read along but i had problem using tor like i use to on windows but you guys saved my ***. i am falling in love with ubuntu. please if there is any new tip for newbies like me enlighten me.

---

### Post by pkjm17 on 2010-08-16
This is what I got...

```
pat@pat-desktop:~$ sudo service tor restart && sudo service polipo restart
tor: unrecognized service
```

---

### Post by bodhi.zazen on 2010-08-17
IMO the tor bundle is by far the easiest method to run TOR

[http://www.torproject.org/torbrowser/](http://www.torproject.org/torbrowser/)

There is a linux version, works great, very simple to  use.

---

### Post by Oxwivi on 2010-08-18
Tor bundles are for newbies to use who don't want to bother with configuration, but I don't like the extra stuff it installs, so I prefer the custom way.

A friend of mine can't access the Tor website (it's blocked where he's at vacation), I introduced Ubuntu to him and he needed proxy as well. So anyway, I compiled Tor from source code in to .deb files to send it to him, and installed it from the .deb  myself to try it out. In the direct installation, start/stoping tor was done from:
```
etc/init.d/Tor/
```

However, installing from my compiled .deb allowed me start it like the other softwares, just by typing it's name in the terminal. When installed directly, it booted at start up (required BUM to stop this), but installation from .deb didn't. What do you guys think?

---

### Post by clementeb on 2010-08-18
Hi,  I am getting crazy here. No matter what way I try, I cannot install. I tried from source, but it told me libevent was not there although it was, then adding the repositories, but I always get the following message: tor:  Depends: tsocks  but it is not installable  Recommends: socat  but it is not installable  Recommends: tor-geoipdb but it is not going to be installed  What can I do? Thank you for any suggestion

---

### Post by bodhi.zazen on 2010-08-18
> **Oxwivi said:**
> Tor bundles are for newbies to use who don't want to bother with configuration, but I don't like the extra stuff it installs, so I prefer the custom way.

Interesting you say that, then ask for assistance with customization.

If you compiled for source you will need to write a custom init script.

> **clementeb said:**
> Hi,  I am getting crazy here. No matter what way I try, I cannot install. I tried from source, but it told me libevent was not there although it was, then adding the repositories, but I always get the following message: tor:  Depends: tsocks  but it is not installable  Recommends: socat  but it is not installable  Recommends: tor-geoipdb but it is not going to be installed  What can I do? Thank you for any suggestion

Did you try the tor bundle ?

Did you try this page ?

[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

---

### Post by rookcifer on 2010-08-18
I am amazed so many have such a hard time installing Tor.  It's really quite simple.  

First you need to add the Tor repo to your /etc/apt/sources.list.  Add the following lines (Ubuntu lucid users only):

```
deb http://deb.torproject.org/torproject.org lucid main
deb-src http://deb.torproject.org/torproject.org lucid main
```

Second, you need to add the key:

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```

Third, update your repo list and then install tor:

```
sudo apt-get update && sudo apt-get install tor tor-geoipdb
```

Fourth, install polipo:

```
sudo apt-get install polipo
```

Fifth, configure polipo:

Go to [this link]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf") and copy everything.  Then open /etc/polipo/config and delete everything there.  Then replace it with what you just copied from the above link (you will need to open the config file with sudo privs).

Sixth, restart polipo and tor:

```
sudo service polipo restart && sudo service tor restart

```

Seventh.  Install Torbutton from the Mozilla extensions page.

Eigth: Make sure Tor works by turning Torbutton on and then visiting [this link.]("https://check.torproject.org/")

---

### Post by bodhi.zazen on 2010-08-18
FYI : You do NOT need polipo (or any other proxy) to use the TOR network.

FYI: If you want adblock (tor is IMO slow enough that I do not want to DL adds) use privoxy (or bfilter) rather then polipo.

Did I mention the TOR bundle ? It is simple to use and very feature rich.

---

### Post by rookcifer on 2010-08-18
> **bodhi.zazen said:**
> FYI : You do NOT need polipo (or any other proxy) to use the TOR network.

True but it's recommended.

> FYI: If you want adblock (tor is IMO slow enough that I do not want to DL adds) use privoxy (or bfilter) rather then polipo.

Privoxy is deprecated.  The Tor developers recommend using Polipo instead of Privoxy.  For one it's much faster. It's why they list Polipo (and not Privoxy) in the installation instructions on their website.

From the Tor FAQ:

> **Why do we need Polipo or Privoxy with Tor? Which is better?**

The first question is, "why a http proxy at all?"

The answer is, because Firefox SOCKS layer has hard-coded timeouts, and other issues,  [https://bugzilla.mozilla.org/show_bug.cgi?id=280661](https://bugzilla.mozilla.org/show_bug.cgi?id=280661). Personally, I don't use an http proxy, I simply let my browser talk to tor via socks directly. The user experience sucks, because you'll receive untold numbers of "The connection has timed out" warnings, because firefox won't wait for Tor to build a circuit. Chrome, Safari, and Arora (amongst others) don't have this problem.

Once Firefox fixes bug 280661, we don't need a http proxy at all. **However, given the current pace of progress on 280661, we may switch to Chrome before the fix occurs.**

The second question is, "why switch from privoxy to polipo?"

Privoxy is fine filtering software that works well for what is it intended to do. However, its user experience is lacking due to it lacking a few features, namely, http 1.1 pipelining, caching most requested objects, and it needs to see the entire page to parse it, before sending it on to the browser. **Lack of these three features is the reason we switched from privoxy to polipo.**

We've received plenty of feedback that browsing with polipo in place of privoxy "feels faster". The feedback indicates that because polipo streams the content to the browser for rendering nearly as fast as it receives it from Tor, the user understands what's going on and will start to read the web page as it loads. Privoxy, necesarily, will load the entire page, parse it for items to be filtered, and then send the page on to the browser. The user experience, especially on a slow circuit, is that nothing happens, the browser activity icon spins forever, and suddenly a page appears many, many seconds later.

If Tor was vastly faster, privoxy's mode of operation wouldn't matter. We're working on making Tor faster. However, purposely showing the user how slow tor can be with privoxy was a huge point of complaint, and not what we intended to do.

---

### Post by pkjm17 on 2010-08-18
> **rookcifer said:**
> I am amazed so many have such a hard time installing Tor.  It's really quite simple.  

First you need to add the Tor repo to your /etc/apt/sources.list.  Add the following lines (Ubuntu lucid users only):

```
deb http://deb.torproject.org/torproject.org lucid main
deb-src http://deb.torproject.org/torproject.org lucid main
```

Second, you need to add the key:

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```

Third, update your repo list and then install tor:

```
sudo apt-get update && sudo apt-get install tor tor-geoipdb
```


This is the output I get after I do ```
sudo apt-get update && sudo apt-get install tor tor-geoipdb
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  tor: Depends: tsocks but it is not installable
       Recommends: socat but it is not installable
E: Broken packages

---

### Post by bodhi.zazen on 2010-08-19
> **rookcifer said:**
> True but it's recommended.

Privoxy is deprecated.  The Tor developers recommend using Polipo instead of Privoxy.  For one it's much faster. It's why they list Polipo (and not Privoxy) in the installation instructions on their website.

Thank you for the clear explanation.

I have been happy with Privoxy as I use it for adblock as well. Personally, in the past, I do not see a performance hit wit Privoxy nor a performance gain with polipo.

With that said, I will look at polipo again.

---

### Post by bodhi.zazen on 2010-08-19
> **pkjm17 said:**
> This is the output I get after I do ```
sudo apt-get update && sudo apt-get install tor tor-geoipdb
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  tor: Depends: tsocks but it is not installable
       Recommends: socat but it is not installable
E: Broken packages

What version of Ubuntu are you using ? from your sig is it 9.04 ? In that case you need to change "lucid" to "karmic" in your sources.list.

Other then that , the instructions worked flawlessly on my machine, there are a few additional steps ...

1. Do you have the universe / multiverse repos enabled ?

2. I highly suggest you follow the steps outlined here :

[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

On the second link, skip step one (which was covered in the first link).

You will need to configure polipo and firefox, the second link has a third like to a polipo config file

[https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf](https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf)

---

### Post by Oxwivi on 2010-08-19
> **bodhi.zazen said:**
> Interesting you say that, then ask for assistance with customization.

If you compiled for source you will need to write a custom init script.
It's my first compilation, and I just followed the instructions. I'm a N00B Ubuntu user, but am used to using Tor how I like it. Anyway, don't need the init.d thing, it's fine the way it is. I was just wondering why it was like that since, as I said, I am new to the technical aspects.

Well, my friend installed it and configured it according to my instructions, but it looks like his network somehow recognises Tor and stop it from connecting. I made him do port scan, but even then the open ones (and only two are open - 8- and 443) refuse to work with Tor. Is there a workaround? I was thinking if it was possible to change the localhost from 127.0.0.1 - any ideas?

---

### Post by completely new on 2010-08-19
Hello, can someone help me with configuring Skype and Pidgin to work with Tor? Thanks.

---

### Post by houndi on 2010-08-19
This way you will not have any of the other person's junk on the computer, think of all the junk programs, files, and other settings that you may not want and how much time

---

### Post by pkjm17 on 2010-08-19
> **bodhi.zazen said:**
> What version of Ubuntu are you using ? from your sig is it 9.04 ? In that case you need to change "lucid" to "karmic" in your sources.list.

Other then that , the instructions worked flawlessly on my machine, there are a few additional steps ...

1. Do you have the universe / multiverse repos enabled ?



Yes, I'm using Lucid Lynx. 
For my sources list, this is what I have in it. (see screenshot)

Do I have the the universe / multiverse repos enabled? I think I did this when I first got Linux and installed it on my computer.

Maybe it has something to do with adding the key? This is my output from adding key.

pat@pat-desktop:~$ gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net

gpg: key 886DDD89: "deb.torproject.org archive signing key" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
pat@pat-desktop:~$ gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
OK

---

### Post by rookcifer on 2010-08-20
> **pkjm17 said:**
> Do I have the the universe / multiverse repos enabled? I think I did this when I first got Linux and installed it on my computer.

Modern Ubuntu versions come out of the box with the multiverse/universe repos enabled by default.  So unless you disabled them for some reason, they should be enabled.

> Maybe it has something to do with adding the key? This is my output from adding key.

pat@pat-desktop:~$ gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net

gpg: key 886DDD89: "deb.torproject.org archive signing key" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
pat@pat-desktop:~$ gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
OK

Nope that looks completely normal.  

TBH, I have no idea what the problem here is.  I followed the steps on a fresh Lucid install and it worked perfectly.  I guess you should post your /etc/apt/sources.list here so we can verify your sources are right.

---

### Post by bodhi.zazen on 2010-08-20
> **bodhi.zazen said:**
> Thank you for the clear explanation.

I have been happy with Privoxy as I use it for adblock as well. Personally, in the past, I do not see a performance hit wit Privoxy nor a performance gain with polipo.

With that said, I will look at polipo again.

Brief update :

I installed TOR on Ubuntu 10.,04 and tested the speed of TOR without any proxy, with privoxy, and with polipo. Polipo was configured with and without adblocking.

The informal results are:

1. TOR without any proxy (just using socks 5 ) is the slowest by far.

2. Privoxy forwarding to socks5 (rather then socks 4 or 4a) is not appreciably faster or slower then polipo.

As a side note, although the mailing list discusses the caching features as an advantage, the defaults for polippo suggested by TOR disable the cache. If you look at the cache you will see why (the cache is certainly a privacy leak). Enabling the cache does not improve speed.

To reproduce this you can try yourself.

Install TOR, privoxy, and polipo. Configure privoxy and polipo to forward to TOR. Configure privoxy to use port 8118 and polipo 8123.

You can easily change your setting s in firefox between TOR , polipo, and privoxy and test load the following sites (these sites have diverse annoyances if you do not have adblock, nothing too bad mind you, but diverse):

[http://linuxpoison.blogspot.com/](http://linuxpoison.blogspot.com/)
[https://check.torproject.org/](https://check.torproject.org/)
[http://www.ebaumsworld.com/](http://www.ebaumsworld.com/)

Note: That last site has lots of images and some popups if you do not add block, some images are NSFW (Not Safe for Work).

Note firefox optimzations (in about:config )

network.http.max-persistent-connections-per-proxy   30
network.http.max-connections                        30
network.http.max-connections-per-server             30
network.http.max-persistent-connections-per-proxy   30
network.http.max-persistent-connections-per-server  30


network.http.pipelining              true
network.http.pipelining.maxrequests  10
network.http.pipelining.ssl          true
network.http.proxy.pipelining        true

IMO some of the information on TOR is a bit dated and honestly I could not appreciate a significant speed difference between privoxy and polipo  hitting those pages and reloading them across several proxies several times.

Testing was performed on a fresh install (plus all updates) of Ubuntu 10.04.1, no extensions in firefox (no adblockplus or NoScript).

The config file for polipo from TOR is tweaked, I advise you use it, but you should review it and understand the changes from the default settings.

Privoxy did not require much of a modification, just forwarding to a socks5 proxy of 9050.

IMO either polipo and privoxy work well, and improve performance on TOR significantly. I di dnot run into any major problems with either proxy, they both work well.

---

### Post by pkjm17 on 2010-08-21
> **rookcifer said:**
> Modern Ubuntu versions come out of the box with the multiverse/universe repos enabled by default.  So unless you disabled them for some reason, they should be enabled.



Nope that looks completely normal.  

TBH, I have no idea what the problem here is.  I followed the steps on a fresh Lucid install and it worked perfectly.  I guess you should post your /etc/apt/sources.list here so we can verify your sources are right.

This is the only thing that's in my /etc/apt/sources.list.Am I missing anything else in it?

deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main

---

### Post by Soul-Sing on 2010-08-21
> This is the only thing that's in my /etc/apt/sources.list.Am I missing anything else in it?

deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main

Thats not ok. You could add these additional sources via [COLOR="Red"]software sources[/COLOR]==> system===>management===>software sources.
You could check your other sources as well via software sources.

---

### Post by pkjm17 on 2010-08-21
> **rookcifer said:**
> I am amazed so many have such a hard time installing Tor.  It's really quite simple.  

First you need to add the Tor repo to your /etc/apt/sources.list.  Add the following lines (Ubuntu lucid users only):

```
deb http://deb.torproject.org/torproject.org lucid main
deb-src http://deb.torproject.org/torproject.org lucid main
```

Second, you need to add the key:

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```

Third, update your repo list and then install tor:

```
sudo apt-get update && sudo apt-get install tor tor-geoipdb
```

Fourth, install polipo:

```
sudo apt-get install polipo
```

Fifth, configure polipo:

Go to [this link]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf") and copy everything.  Then open /etc/polipo/config and delete everything there.  Then replace it with what you just copied from the above link (you will need to open the config file with sudo privs).

Sixth, restart polipo and tor:

```
sudo service polipo restart && sudo service tor restart

```

Seventh.  Install Torbutton from the Mozilla extensions page.

Eigth: Make sure Tor works by turning Torbutton on and then visiting [this link.]("https://check.torproject.org/")

I was able to install Tor and Polipo, and got the Torbutton, however, when I have Tor enabled, and if I click on a link or type a link into the browser, nothing happens.It won't display the page. Any idea why?

---

### Post by mandragor on 2010-08-21
I recommend you take a look in the logfiles for both Tor and Polipo;
/var/log/tor/log
and
/var/log/polipo/polipo.log

Make sure they don't report any errors.

---

### Post by pkjm17 on 2010-08-21
> **mandragor said:**
> I recommend you take a look in the logfiles for both Tor and Polipo;
/var/log/tor/log
and
/var/log/polipo/polipo.log

Make sure they don't report any errors.

It looks there are errors in these log files:

/var/log/tor/log

Aug 21 14:37:53.159 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit 'Amunet3'. Retrying on a new circuit.
Aug 21 14:37:53.160 [notice] Tried for 125 seconds to get a connection to [scrubbed]:80. Giving up.

/var/log/polipo/polipo.log

Established listening socket on port 8118.
Established listening socket on port 8118.
Connect to [www.singlesnet.com:80](www.singlesnet.com:80) failed: General SOCKS server failure
Couldn't read from client: Connection reset by peer

What do I do?

---

### Post by mandragor on 2010-08-21
Tor is failing for some reason, you can restart it and watch the logfile - there
might be a clue as to why.

Did you edit /etc/tor/torrc ?

Are you behind a restrictive firewall?

---

### Post by pkjm17 on 2010-08-22
> **mandragor said:**
> Tor is failing for some reason, you can restart it and watch the logfile - there
might be a clue as to why.

Did you edit /etc/tor/torrc ?

Are you behind a restrictive firewall?

No, I didn't do anything to /etc/tor/torrc. Am I supposed to add something in there?

Anyway, I finally Tor to work... I think I had Vidalia installed and it was probably causing it to fail. Interesting thing...some websites I visit, with Tor enabled, i.e Facebook or Yahoo, the site will be in a different language like German or another different language lol

---

### Post by StoicLion on 2010-09-04
Thanks, rookcifer.  

Your explanation was just what I needed.  I got through the first couple of steps (clumsily because I'm such a newbie to ubuntu) from the Tor site's installation instructions but I couldn't figure out how to change the polipo config file. It was opening up as a read-only version for me.  

So, thanks, you got me through it.  

- Stoic  


> **rookcifer said:**
> I am amazed so many have such a hard time installing Tor.  It's really quite simple.  

First you need to add the Tor repo to your /etc/apt/sources.list.  Add the following lines (Ubuntu lucid users only):

```
deb http://deb.torproject.org/torproject.org lucid main
deb-src http://deb.torproject.org/torproject.org lucid main
```Second, you need to add the key:

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```Third, update your repo list and then install tor:

```
sudo apt-get update && sudo apt-get install tor tor-geoipdb
```Fourth, install polipo:

```
sudo apt-get install polipo
```Fifth, configure polipo:

Go to [this link]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf") and copy everything.  Then open /etc/polipo/config and delete everything there.  Then replace it with what you just copied from the above link (you will need to open the config file with sudo privs).

Sixth, restart polipo and tor:

```
sudo service polipo restart && sudo service tor restart

```Seventh.  Install Torbutton from the Mozilla extensions page.

Eigth: Make sure Tor works by turning Torbutton on and then visiting [this link.]("https://check.torproject.org/")

---

### Post by aboodk on 2010-09-20
> **rookcifer said:**
> I am amazed so many have such a hard time installing Tor.  It's really quite simple.  

First you need to add the Tor repo to your /etc/apt/sources.list.  Add the following lines (Ubuntu lucid users only):

```
deb http://deb.torproject.org/torproject.org lucid main
deb-src http://deb.torproject.org/torproject.org lucid main
```Second, you need to add the key:

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```Third, update your repo list and then install tor:

```
sudo apt-get update && sudo apt-get install tor tor-geoipdb
```Fourth, install polipo:

```
sudo apt-get install polipo
```Fifth, configure polipo:

Go to [this link]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf") and copy everything.  Then open /etc/polipo/config and delete everything there.  Then replace it with what you just copied from the above link (you will need to open the config file with sudo privs).

Sixth, restart polipo and tor:

```
sudo service polipo restart && sudo service tor restart

```Seventh.  Install Torbutton from the Mozilla extensions page.

Eigth: Make sure Tor works by turning Torbutton on and then visiting [this link.]("https://check.torproject.org/")



Thank you rookcifer for your explanation, Although I am having a problem when trying to add the GPG key****, this is the output that I get :

abood@abood-laptop:~$ gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


I have also tried the mit.edu keyserver suggested previously but it gave me the same results.

BTW : I'm not sure if this is related but i'm using a 64 bit system.

---

### Post by jaysl on 2010-09-27
aboodk, have a look here, could be your firewall blocking.
[http://ubuntuforums.org/showthread.php?t=1492290](http://ubuntuforums.org/showthread.php?t=1492290)

My own problem is key not found.
```
$ gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpgkeys: key 886DDD89 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

I get the same using other servers.
```
$ gpg --keyserver pgp.mit.edu --recv 886DDD89
gpg: requesting key 886DDD89 from hkp server pgp.mit.edu
gpgkeys: key 886DDD89 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

Does anybody know why I'm getting key not found?

edit: I've now installed gui-apt-key and added the key through that no problem. No idea why it didn't work from the terminal with gpg.

---

### Post by sideshowmel on 2010-09-27
> **rookcifer said:**
> First open a terminal and cut and paste this command:

```
sudo echo 'deb http://deb.torproject.org/torproject.org lucid main' > /etc/apt/sources.list && gpg --keyserver keys.gnupg.net --recv 886DDD89 && gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - && sudo aptitude update && sudo aptitude install tor tor-geoipdb polipo
```

The above installs the official Tor project repo and adds their key.

Now edit the polipo config file like so:

```
sudo gedit /etc/polipo/config
```

Now *delete everything* in that file and replace it with [this configuration]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf").  Be sure to hit "save" on gedit and then exit it.  This config file is directly from the official Tor website.

Now type this:

```
sudo service tor restart && sudo service polipo restart
```

Then in Firefox install the "torbutton" add-on.

You now have a fully functional Tor setup ready for action. :guitar:

DON'T DO THIS!!!!  I had to completely regenerate my sources.list file from scratch (see the > above where should be >>?).

---

### Post by bodhi.zazen on 2010-09-27
See this page :

[http://bodhizazen.net/Tutorials/tor/](http://bodhizazen.net/Tutorials/tor/)

---

### Post by rookcifer on 2010-09-28
> **sideshowmel said:**
> DON'T DO THIS!!!!  I had to completely regenerate my sources.list file from scratch (see the > above where should be >>?).

Why would you need to do that?  If you don't want something there just open a text editor and remove it.  Or, better yet, just create a "tor.list" inside of /etc/apt/sources.list.d.  I should have probably done it that way when I made the little tutorial since this seems to be the new way things are done.

---

### Post by bodhi.zazen on 2010-09-28
> **rookcifer said:**
> Why would you need to do that?  If you don't want something there just open a text editor and remove it.  Or, better yet, just create a "tor.list" inside of /etc/apt/sources.list.d.  I should have probably done it that way when I made the little tutorial since this seems to be the new way things are done.

I think the point is the diference between > an >>

If you use one > , it over writes the file. Two >> appends your file.

So your step "sudo echo 'deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main'  > /etc/apt/sources.list"

The single > overwrites the entire file. Thus sources list needed to be restored.

Another small point, you can not 

"sudo echo 'deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main'  > /etc/apt/sources.list" , sudo will not allow a redirect like this.

See this :

```
bodhi@lucid:~$ tail -n 1 /etc/apt/sources.list
deb http://deb.torproject.org/torproject.org lucid main

[COLOR=darkred]#See how your command fails?[/COLOR]
bodhi@lucid:~$ sudo echo 'this fails' > /etc/apt/sources.list
[COLOR=darkred]bash: /etc/apt/sources.list: Permission denied[/COLOR]

# Just to confirm that =)
bodhi@lucid:~$ tail -n 1 /etc/apt/sources.list
deb http://deb.torproject.org/torproject.org lucid main

[COLOR=darkred]# See how a single > overwrites the entire file ?[/COLOR]
bodhi@lucid:~$ sudo bash -c "echo 'this works' > /etc/apt/sources.list"
bodhi@lucid:~$ tail -n 1 /etc/apt/sources.list
this works

[COLOR=darkred]# Ohhh Noooooo !!!!
bodhi@lucid:~$ cat /etc/apt/sources.list
this works[/COLOR]
```What you want is to use the bash -c trick I showed you or tee, but with a >> rather then a >

```
[COLOR=darkgreen]#This works
bodhi@lucid:~$ sudo bash -c "echo 'this works' >> /etc/apt/sources.list"
bodhi@lucid:~$ tail -n 3 /etc/apt/sources.list

deb http://deb.torproject.org/torproject.org lucid main
this works[/COLOR]
```Notice the redirect (bash -c) and two >> 

:twisted:

---

### Post by rookcifer on 2010-09-29
> **bodhi.zazen said:**
> I think the point is the diference between > an >>

If you use one > , it over writes the file. Two >> appends your file.

So your step "sudo echo 'deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main'  > /etc/apt/sources.list"

The single > overwrites the entire file. Thus sources list needed to be restored.

Another small point, you can not 

"sudo echo 'deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main'  > /etc/apt/sources.list" , sudo will not allow a redirect like this.

See this :

```
bodhi@lucid:~$ tail -n 1 /etc/apt/sources.list
deb http://deb.torproject.org/torproject.org lucid main

[COLOR=darkred]#See how your command fails?[/COLOR]
bodhi@lucid:~$ sudo echo 'this fails' > /etc/apt/sources.list
[COLOR=darkred]bash: /etc/apt/sources.list: Permission denied[/COLOR]

# Just to confirm that =)
bodhi@lucid:~$ tail -n 1 /etc/apt/sources.list
deb http://deb.torproject.org/torproject.org lucid main

[COLOR=darkred]# See how a single > overwrites the entire file ?[/COLOR]
bodhi@lucid:~$ sudo bash -c "echo 'this works' > /etc/apt/sources.list"
bodhi@lucid:~$ tail -n 1 /etc/apt/sources.list
this works

[COLOR=darkred]# Ohhh Noooooo !!!!
bodhi@lucid:~$ cat /etc/apt/sources.list
this works[/COLOR]
```What you want is to use the bash -c trick I showed you or tee, but with a >> rather then a >

```
[COLOR=darkgreen]#This works
bodhi@lucid:~$ sudo bash -c "echo 'this works' >> /etc/apt/sources.list"
bodhi@lucid:~$ tail -n 3 /etc/apt/sources.list

deb http://deb.torproject.org/torproject.org lucid main
this works[/COLOR]
```Notice the redirect (bash -c) and two >> 

:twisted:


Yes, you're correct.  I made a boo boo here. :oops:  I have corrected it in my original post.  Instead of appending it to sources.list, I just made it so that it creates a new tor.list file in /etc/apt/sources.list.d.  If this is not satisfactory, let me know.

---

### Post by bodhi.zazen on 2010-09-29
> **rookcifer said:**
> Yes, you're correct.  I made a boo boo here. :oops:  I have corrected it in my original post.  Instead of appending it to sources.list, I just made it so that it creates a new tor.list file in /etc/apt/sources.list.d.  If this is not satisfactory, let me know.

Not a problem, we all, or at least I have made my share of mistakes. I hope I pointed this out to you as educationally as possible.

Yes using /etc/apt/sources.list.d works and will likely become the preferred method, nice touch.

---

### Post by fisbike on 2010-10-01
Fifth, configure polipo:

Go to [this link]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf")  and copy everything.  Then open /etc/polipo/config and delete  everything there.  Then replace it with what you just copied from the  above link (you will need to open the config file with sudo privs).

I wasnt able to do this step cause I cant delete everything in /etc/polipo/config and the delete word is greyed out.  How?

---

### Post by bodhi.zazen on 2010-10-01
> **fisbike said:**
> Fifth, configure polipo:

Go to [this link]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf")  and copy everything.  Then open /etc/polipo/config and delete  everything there.  Then replace it with what you just copied from the  above link (you will need to open the config file with sudo privs).

I wasnt able to do this step cause I cant delete everything in /etc/polipo/config and the delete word is greyed out.  How?

You have to edit the file as root

```
gksu gedit /etc/polipo/config
```

Or you can use nano

```
sudo nano /etc/polipo/config
```

Or vim

```
sudo -e /etc/polipo/config
```

---

### Post by madmax75 on 2010-11-18
I followed the instructions from the Tor website

[https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian)

[https://www.torproject.org/docs/tor-doc-unix.html.en#polipo](https://www.torproject.org/docs/tor-doc-unix.html.en#polipo)

and it seems to be working just fine for me. No problems as far as I can tell.

Using 10.04.1 LTS

---

### Post by zaphodbblx on 2010-11-27
The problem I get is it cant seem to find the file to execute and I downloaded it through synaptic too

---

### Post by cariboo on 2010-11-27
Most executables are in /usr/bin, You can also find were an application is installed by going to Synaptic, highlight the package, and click Properties->Installed files.

---

### Post by zaphodbblx on 2010-11-28
why would a program I downloaded through synaptic loose parts of its self though. thats a first for me in 3 yrs of using Linux full time. thanks I will look there again though

---

### Post by justinjedlawton on 2011-07-24
> **rookcifer said:**
> First open a terminal and cut and paste this command:

```
sudo echo 'deb http://deb.torproject.org/torproject.org lucid main' > /etc/apt/sources.list.d/tor.list && gpg --keyserver keys.gnupg.net --recv 886DDD89 && gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - && sudo aptitude update && sudo aptitude install tor tor-geoipdb polipo
```The above installs the official Tor project repo and adds their key.

Now edit the polipo config file like so:

```
sudo gedit /etc/polipo/config
```Now *delete everything* in that file and replace it with [this configuration]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf").  Be sure to hit "save" on gedit and then exit it.  This config file is directly from the official Tor website.

Now type this:

```
sudo service tor restart && sudo service polipo restart
```Then in Firefox install the "torbutton" add-on.

You now have a fully functional Tor setup ready for action. :guitar:


i whent to the new conf. and it gave me a 404

---

### Post by sev1 on 2011-09-25
[FONT=Arial]I've read & reread the post and am having a different issue getting TOR to work. No problems with the install (TOR w/ Polipo - no Torbutton), but:

ss -aln | grep 9050 gets:  0      128                    127.0.0.1:9050

the ubuntu guide to setting up TOR says command should get one of the following:
[FONT=monospace]
[/FONT][/FONT][FONT=Arial]0  0  :::950  :::*
0  0   *:950   *:*

Can anyone tell me if the fact that I'm getting '128' instead of '0' is causing the problem? Also, I've started, stopped, restarted TOR from 
terminal as suggested in the post, and I don't see it running in sys monitor. Why does TOR not seem to be running?  [/FONT]

---

