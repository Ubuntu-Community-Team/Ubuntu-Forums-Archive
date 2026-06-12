---
title: "Any way to assign specific apps or a terminal profile to use tor?"
date: 2016-01-16
forum: Security
---

### Post by Hitman_Forhire on 2016-01-16
I've looked around quite a bit and cruised the bash man pages and /home/$user/.bashrc even for an out there, but I can't seem to find a way to specifically use JUST my gnome terminal or any one terminal app with tor. I already run one of my web browsers and a few other selective applications through tor. I prefer not to use tor system wide as many things I do I am ok with no anonymity and I need the speed that the tor network doesn't offer for these non-anonymized applications. I do however want to be able to either select a certain users shell or choose a specific configured profile when I feel the need to use certain tools anonymously. 

Any help would be greatly appreciated, and of course I already have a happily running tor setup I just need the ability to use ONE shell, user account, or xterm app through that existing tor setup; Thanks again.

---

### Post by bashiergui on 2016-01-16
I would use Tails for anything you want routed over Tor. You can manually configure anything to go over Tor on Ubuntu but not all apps will remain private. DNS leakage is an issue typically. Set up two machines to use simultaneously. I don't know of a way to run both on a machine simultaneously without leaks.

---

### Post by Hitman_Forhire on 2016-01-16
...I saw someone bring this up a while back and evidence to the contrary was explained here. As it points out even if using Tails, the dns server can still log your request however you use TOR.

> 
**submitted by Gnollsy**
I've been playing around on Tor recently. **Specifically I'm running off a Tails bootable USB drive**. I was recently made aware of [www.dnsleaktest.com](www.dnsleaktest.com) - where you can run a test to see who's "watching" you. The website says: "This page shows the DNS servers that your computer is using to resolve DNS names...
Is this something that I should be worried about? Are those DNS servers actually able to track what I'm doing, despite the whole idea of anonymity on Tor?
Any help is greatly appreciated. Thanks!

**[–]deathfantasy **
Tor should mask your DNS requests when used correctly. The DNS servers can know what you are connecting to, but they cannot know who you are, just by looking at those requests.

**[–]alexpeterson91 **
I'm not an expert on Tor but my understanding is that it's not actually anonymous, its simply infeasible to track someone through the tor network, due to the several random relays your client connects through. All of those connections are encrypted further making it technologically infeasible to find the source. So all of those DNS servers that show up are just random DNS servers from those random nodes you connected through. They have absolutely no idea where you are or who you are due to the tor network traffic constantly changing routes and encryption. For a test, try to run the test on tor, then change your identity and try again, my assumption is that you'll have an entirely new set of servers tracking your new path, but these servers still do not know who you are, nor where you are.
 Tor doesn't make you invisible, it just lets you hide among the millions and millions of clients on the web.


**[–]Gnollsy[S] **
This is along the lines that I was thinking, but what's confusing me is why there are so many? Isn't the idea of the Tor network that, from any given node _*only the source and destination can be determined*_? Like, you couldn't trace beyond one node in either direction, and I believe Tor bounces your signal at least three separate times to make it anonymous.
Therefor I wouldn't expect to see so many. Two would make sense in my mind, unless the additional servers are from others using ME as a node? Maybe that's it?


**[–]eclecticApe**
Funny I had this exact question a half year ago...
Basically the way tor handles DNS requests is to balance them throughout the network... it is not a "dns leak"... **the developers are obviously aware of DNS and its potential in revealing your location... **therefore [B][U]TOR is configured to process DNS requests throughout the network, that is why you are seeing multiple DNS servers being queried at dnsleaktest.com
No worries[/U][/B], do an ipconfig /flush on your computer, and your dns queries will be safely and anonymously routed throughout the network.


From what I've researched Tails is simply a small distro that has several pre-configured tools all utilizing the already setup tor network settings. The *extra* appeal beyond just running tor locally on your current OS is the fact that it's a live-distro so it saves no cache locally in swap, firewall logs, dns cache, etc...to know which node you've connected to. When the machine is restarted or powered down, any and all changes/cache/logs are erased because they are only temporarily stored in RAM, unless you proactively tell Tails to do it otherwise.

***From the Tails site:***
> 
"**Use anywhere but leave no trace**

Using Tails on a computer doesn't alter or depend on the operating system installed on it. So you can use it in the same way on your computer, a friend's computer, or one at your local library. After shutting down Tails, the computer will start again with its usual operating system.

Tails is configured with special care to not use the computer's hard-disks, even if there is some swap space on them. The only storage space used by Tails is in RAM, which is automatically erased when the computer shuts down. So you won't leave any trace on the computer either of the Tails system itself or what you used it for. That's why we call Tails "amnesic".

This allows you to work with sensitive documents on any computer and protects you from data recovery after shutdown. Of course, you can still explicitly save specific documents to another USB stick or external hard-disk and take them away for future use."

Just thought I would help anyone who is seeing this to understand the elements in discussion, in case they weren't aware. I really appreciate the response but as I indicated initially I am aware I can run TOR for every connection my entire machine utilizes in a blanket effect, however I choose to run some applications on the clear and some inside of the TOR network. I use chrome in the free and firefox is configured to connect to the net via TOR. This is a permanent configuration. I would just like to know if anyone is aware of a way to selectively through either a gnome-terminal client profile, a single configured additional user, or just a specific xterm emulator; To have the ability to use a shell locally both in the free[normal net connection] if configured that way, as well as another[user/xterm client/xterm profile] through TOR if I choose. Thanks for any help.

---

### Post by Hitman_Forhire on 2016-01-16
So the culprit was my lack of investigating further into the bash documentation. By default bash is installed of course but there is a seperate package for much of the documentation and all of the example configs for .bashrc....Once I figured this out, I simply installed it like so

```
**root@SPARTAN:/home/spartan#** apt-cache search bash | grep examples
**bash-doc** - Documentation and examples for the GNU Bourne Again SHell
**bash-builtins** - Bash loadable builtins - headers & examples

**root@SPARTAN:/home/spartan#** apt-get -y install bash-doc

```

After combing the full set of configurations & examples I realized how to solve my problem. Where I initially looked for the answer was the solution, in the /home/$user/.bashrc file you can annotate a proxy for every per user and instance of all network activity if you like. So that I can run an single terminal window which all commands for the web are routed through tor while also having another terminal windows open *simultaneously* with my typical free-and-clear network I created an additional user and added an entry into that users .bashrc. This way if I want to use terminal with tor, I just 'login' through the terminal as the alternate user and all connections for that user are routed through my existing tor setup. Bingo!

Simply add this line to your .bashrc and at every login this will take effect, making it a permanent change essentially.
```

export SOCKS_SERVER=127.0.0.1:9150
```
I also found that if you would like to execute a random or single command through a proxy/socks server it can be done at the prompt.
```
me@home$proxy-exec --type sock5 --server 127.0.0.1:9150 -- ping blah
```
It seems that once I thoroughly tested this, some applications do not read the SOCKS_SERVER config so they therefore wont connect through tor making this an incomplete solution...
Applications do however read the HTTP_PROXY= command but a small workaround allows connecting to the socks server using it.
```
export http_proxy=socks5://127.0.0.1:8080 https_proxy=socks5://127.0.0.1:8080

```
For the sake of thoroughness I wasn't willing to settle for this solution know that there may be 1 application that wouldn't reference it, I want a flawless option.
_**Evolution 3** _
I then discovered proxychains, you can use this by setting it up for your tor connection and command after 'proxychains' goes through as so
```
me@home$proxychains-ng ping google.com
```

I've seen that there can be endpoint issues because the exit node on the tor server can occassionally make nmap scans fail, the solution to this is simply adding one or more regular non-tor proxies to the proxychains conf file listed AFTER the tor proxy.

```
# defaults set to "tor"
socks4  127.0.0.1 9050
socks4 115.71.237.212 1080
```
So an nmap scan executed with proxychains with this configuration would travel through the --> tor network --> the public proxy --> then to the host being scanned- then back again. Creating multiple layers of anonymity can also be achieved by 'chaining' many proxies after the tor network in that list making it very difficult to track an individual wishing to liberate their privacy rights.

Sorry to sort of answer my own question but I feel this is a good bit of information to share that I couldn't find existing on the site, all comments and improvements would be appreciated.

---

### Post by bashiergui on 2016-01-18
Nmap over chained proxies- that must be painfully slow. You said you tested - how? Did you sniff packets? Really curious what other apps you're routing over tor. You using the tor browser bundle or did you configure firefox yourself?

---

