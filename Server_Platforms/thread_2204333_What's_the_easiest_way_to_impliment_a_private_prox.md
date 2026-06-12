---
title: "What's the easiest way to impliment a private proxy?"
date: 2014-02-07
forum: Server Platforms
---

### Post by RedShoeRider on 2014-02-07
Good Day, All:

I've done a bit of searching and came up with some answers from 2008ish, so I'm wondering if there's a better/newer way to go about things. I'm a big hardware guy, but I'm just getting into the meat of the server world. 

Here's what I'm running: 13.10 server (headless) on an HP DL360 behind an IPCop/Firebox firewall. Connectivity is on cable with a static IP with port 80 available.
What I'd like to do: We spend a fair amount of time on the road for business, so I'd love to have my own private proxy server here at home that I could use to securely relay though when I'm in a hotel/hotspot/whatever. I realize I could do this with a VPN, but I'd prefer not to as more than a few places block that. 

In a perfect world, I'd head to www.<mywebsitehere>.com, where I'd be presented with just a blank page asking for a username and password. Upon logging in, I'd have access to a screen where I could type in whatever address I wanted to go to, and away I went, all over https. 

I realize there's a ton of configuration to be done with this, along with hardening the server in the first place, but just program-wise, how would you approach this? I know there are about a dozen ways, but what does the community think would be the easiest/most hardened/fewest headaches method? 

My thanks for the thoughts!
-Red

---

### Post by devine.steve on 2014-02-07
Well if you want to proxy your connections Squid is your best bet. What are you trying to do? If it's increasing your security I don't think this will help much.

---

### Post by RedShoeRider on 2014-02-08
Indeed, I think Squid would be a good start, as that seems to be everyone's go-to for a proxy. My goal is a private https proxy, basically, in which I'd go to one my website, so www.<mysite>.com, log in, then use the server as a proxy to go out to the world. So, I figure I'll need Squid(?), Apache(?), and....?.... That's really the question: what combination of stuff would someone who has a lot more experience than I have start with.

---

### Post by Lars Noodén on 2014-02-08
If you have SSH access to the machine that you want to use as a proxy you can very easily run a SOCKS proxy.  All it takes is one line in the shell, using the -D option with ssh.

```

ssh -D 4321 *xx.yy.zz.aa*

```

and then setting one option in Firefox:

Edit->Preferences->Advanced->Network->Connection->Manual Proxy->SOCKS Host-> port 4321, localhost

That will then proxy all traffice from Firefox, both HTTP and HTTPS, via your SSH server.  When you are done, just close the SSH session and set Firefox back to 'No proxy' or whatever you had before.

---

### Post by volkswagner on 2014-02-08
+1 for SSH and SOCKS.

You can also do this with Chrome browser without changing global settings.  you can add it to launch parameter.

If you are using a Windows client you'll have to start a putty session first, then launch Chrome like this:

I got help from [here]("http://blag.not.all-that-useful.info/rmation/2011/03/12/using-a-socks-proxy-with-google-chrome/").

```
chrome.exe --proxy-server="socks5://<host:port>"
```

---

