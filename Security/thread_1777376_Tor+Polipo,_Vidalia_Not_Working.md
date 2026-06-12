---
title: "Tor+Polipo, Vidalia Not Working"
date: 2011-06-07
forum: Security
---

### Post by Bryant.GhostInTheMachine on 2011-06-07
I just recently installed Tor again on my new Natty install along with Vidalia. It was working initially, but for some reason it has ceased to function within the last 24 hours. When I start Tor (either from the command-line or Vidalia) and go to check.torproject.org, it says that Tor isn't running. (I don't use Torbutton with Firefox, if that makes any difference. I use FoxyProxy, but the settings look fine to me. It was working only yesterday.) I've checked the config files for Polipo and Tor, and I've checked my Vidalia settings more times than I can count. It all looks perfectly satisfactory.

I'm sure that it's not my firewall, Tor/Polipo configurations, or Vidalia settings. When I launch Tor with Vidalia and check the logs, everything works just fine and it says I'm connected. The only thing I can think of is that it might be a FoxyProxy issue or a problem with check.torproject.org, but the settings for FoxyProxy look okay and check.torproject.org hasn't malfunctioned in the past.

I've purged and reinstalled Tor, Vidalia, and Polipo and restored their config files and settings to the defaults, but still to no avail. My current malfunctioning Tor configuration is identical to my old and functional one, so far as I can tell.

Does anyone have a solution?

---

### Post by Bryant.GhostInTheMachine on 2011-06-07
Nevermind, issue solved. I went through the Polipo config file and realized that the 'default' I had restored it to was faulty. I replaced it with a fresh copy from the Torproject website.

---

### Post by abdulrahman alhussni on 2011-07-09
hello .. 
please ... can u tell me how can u get it work .... 
tor + vidalia + polipo = a nightmare to me ... 
its about a week of trying to make them work ... im hopeless ... :(
please help .... 


look at this .... if u please 
[http://ubuntuforums.org/showthread.php?t=1800685](http://ubuntuforums.org/showthread.php?t=1800685)

---

### Post by Bryant.GhostInTheMachine on 2011-07-24
Sorry this has taken so long to reply to, I haven't logged in for ages...
I've attached a .zip file called 'Advanced Security Setup'. It contains a step-by-step how-to manual I wrote on setting up system security for paranoid nuts like me, along with all of the necessary scripts and config files. If you don't want to bother with all of the extra security and just want to set up Tor, open the 'Advanced Security Setup' text file and scroll down to the section labeled 'Internet Privacy and Security'. It details how I set up Tor on my computer, along with some other useful instructions on setting up additional internet privacy stuff. Feel free to message me with any questions and queries you may have.

---

### Post by flgnk on 2011-08-04
Hi,

I just wanted to say thanks for the tips above.
I found it very useful. I'm a little bit new to Tor and was having problems getting Tor, Vidalia and Browser working together.
I think I was most of the way there. I had Vidalia running but I missed out on pointing Vidalia to the torrc file. Also I was having problems with Tor button. For some reason even though I install and restart it was not appearing in Firefox.
So I set up a new user profile in Firefox specifically for Tor use.
I installed the addons you suggested although I must be doing something wrong with Foxyproxy as I couldnt get it to work.
However Torbutton is now working fine under that new Firefox profile so I'm not to worried.
Out of curiosity why do you prefer to use Foxyproxy over Torbutton?
And are there any additional settings you would recommend for a wifi router.
I have port forwarding set up on 9030 and 9001.

Thanks Again

---

### Post by flgnk on 2011-08-04
Ok I'm still getting some a problem showing up..

Here is the output from the message log. It just keeps repeating this over and over. Any ideas?


Aug 04 18:38:10.018 [Info] resolve_my_address(): Guessed local hostname 'CRZ' resolves to a private IP address (127.0.0.1).  Trying something else.
Aug 04 18:38:10.019 [Info] resolve_my_address(): Interface IP address '192.168.1.130' is a private address too. Ignoring.
Aug 04 18:38:10.023 [Info] resolve_my_address(): Address 'CRZ' resolves to private IP address '127.0.0.1'. Tor servers that use the default DirServers must have public IP addresses.
Aug 04 18:38:10.023 [Info] router_pick_published_address(): Could not determine our address locally. Checking if directory headers provide any hints.
Aug 04 18:38:10.024 [Info] resolve_my_address(): Guessed local hostname 'CRZ' resolves to a private IP address (127.0.0.1).  Trying something else.
Aug 04 18:38:10.025 [Info] resolve_my_address(): Interface IP address '192.168.1.130' is a private address too. Ignoring.
Aug 04 18:38:10.026 [Info] resolve_my_address(): Address 'CRZ' resolves to private IP address '127.0.0.1'. Tor servers that use the default DirServers must have public IP addresses.
Aug 04 18:38:10.027 [Info] router_pick_published_address(): Could not determine our address locally. Checking if directory headers provide any hints.
Aug 04 18:38:10.027 [Info] update_consensus_router_descriptor_downloads(): 0 router descriptors downloadable. 0 delayed; 2494 present (0 of those were in old_routers); 0 would_reject; 0 wouldnt_use; 0 in progress.
Aug 04 18:38:10.028 [Info] resolve_my_address(): Guessed local hostname 'CRZ' resolves to a private IP address (127.0.0.1).  Trying something else.
Aug 04 18:38:10.029 [Info] resolve_my_address(): Interface IP address '192.168.1.130' is a private address too. Ignoring.
Aug 04 18:38:10.030 [Info] resolve_my_address(): Address 'CRZ' resolves to private IP address '127.0.0.1'. Tor servers that use the default DirServers must have public IP addresses.
Aug 04 18:38:10.030 [Info] router_pick_published_address(): Could not determine our address locally. Checking if directory headers provide any hints.
Aug 04 18:38:10.031 [Info] routerlist_remove_old_routers(): We have 2617 live routers and 1253 old router descriptors.
Aug 04 18:38:10.032 [Info] resolve_my_address(): Guessed local hostname 'CRZ' resolves to a private IP address (127.0.0.1).  Trying something else.

---

### Post by Bryant.GhostInTheMachine on 2011-08-09
I've never seen this issue before on my Tor setup, so I'm not sure if i can help you with this one, but it looks like Tor is having issues figuring out the ip address for your computer/'net interface. I can't make heads, tails, or anything in between out of it... have you ever modified your ip address or network interface settings? That could be the issue, but I can't be sure... the the specifics of the output given are lost on me, but that's the general idea I get from looking at it.

To answer your previous question, I use foxyproxy because I can set up url patterns that tell foxyproxy when to and when not to load a webpage through tor. That way it will load everything but certain sites (such as my online bank account, facebook, etc.) through my tor connection. Websites like banking accounts, social networking, and the rest tend to boot one out if one uses Tor because of security concerns. Torbutton works,  but I like the greater degree of flexibility that foxyproxy gives me. Besides, I have a newer version of firefox with which Torbutton doesn't cooperate well.

---

### Post by Bryant.GhostInTheMachine on 2011-08-09
And port forwarding isn't really necessary. At least, I've never set it up and Tor seems to chug along perfectly fine without it. I'd suggest disabling the port forwarding you set up unless you absolutely need it, as it could present a security hole to a sufficiently determined attacker.

---

### Post by windeguy on 2011-08-10
Hello Bryant, 

Thank you for posting the information since I too have not had any luck getting TOR and Vidalia to work in Ubuntu 10.04.  One problem when I open Vidalia is taht it gives me an error message that TOR cannot connect because it thinks TOR is already running. TOR is not already running. Here is what Vidalia reports: 

[B]Aug 10 09:45:29.366 [Notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Aug 10 09:45:29.366 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Aug 10 09:45:29.367 [Notice] Opening Socks listener on 127.0.0.1:9050
Aug 10 09:45:29.367 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Aug 10 09:45:29.367 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Aug 10 09:45:29.367 [Error] Reading config failed--see warnings above.[/B]


And there seems to be a problem with the existing config file, which already looks like the one you posted, by the way. When I look at the torrc file you suggest using in the files you posted, it appears that all of the lines, except for two,  are commented out. Is that true? I don't know what, if anything else needs to be changed.

---

### Post by chrismack88 on 2011-08-13
Windeguy,
You are not alone. I am receiving that exact message from my Vidalia also. I hope to find a solution to this problem. Thanks for all your hard work everyone. Ubuntu is awesome.

---

### Post by windeguy on 2011-08-13
> **chrismack88 said:**
> Windeguy,
You are not alone. I am receiving that exact message from my Vidalia also. I hope to find a solution to this problem. Thanks for all your hard work everyone. Ubuntu is awesome.

It is frustrating that this is so difficult to install correctly. 
For the moment I have to use Win7 to do what I need with Vidalia, but I really hope an Ubuntu solution can be worked out. (The Vidalia package installed very easily in WinXP and Win7.)

---

### Post by Bryant.GhostInTheMachine on 2011-08-18
It looks to me like port 9050 is already in use by another application rather than tor, though I don't see how that could happen. Try using the system monitor to check for any already running Tor processes, kill them if they exist, and fire up tor again. 

Could you copy/paste your /etc/tor/torrc file into this thread so I can review it? It seems that it could be an issue with the config file.

I had this same issue when I first set this thing up. Its been so long that I forgot exactly how I fixed it... But the entire solution I employed is posted as a .zip file above. If you haven't done so, give that a shot as suggested in the post. If that hasn't worked for you, well, I haven't the faintest idea how to solve the issue. I'll check over your config for any conflicts, but I'm not entirely positive that that is the problem.

Note: There should only be two lines uncommented in your entire /etc/tor/torrc file:

SocksPort 9050

And:

SocksListenAddress 127.0.0.1

That's all I can think of at the moment. I'll work on this over the weekend and I'll get back to you if I find an answer.

[EDIT]:
Vidalia should install as easily in ubuntu as in windows. It's just the configuration that's hard. try following my steps exactly as described in the document I uploaded.

---

### Post by windeguy on 2011-08-18
Bryant, it looks like the only two lines not commented out in the torrc file are correct as you indicated.  I have never seen an instance of TOR already running when looking at the System Monitor. Also I did look at your Advanced Security Setup recommendations and I believe I followed them correctly with regards to setting up TOR. Thanks for your help and any further suggestions.  Here is the /etc/tor/torrc file: 

## Configuration file for a typical Tor user
## Last updated 12 April 2009 for Tor 0.2.1.14-rc.
## (May or may not work for much older or much newer versions of Tor.)
##
## Lines that begin with "## " try to explain what's going on. Lines
## that begin with just "#" are disabled commands: you can enable them
## by removing the "#" symbol.
##
## See 'man tor', or [https://www.torproject.org/tor-manual.html](https://www.torproject.org/tor-manual.html),
## for more options you can use in this file.
##
## Tor will look for this file in various places based on your platform:
## [https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#torrc](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#torrc)


## Replace this with "SocksPort 0" if you plan to run Tor only as a
## relay, and not make any local application connections yourself.
SocksPort 9050 # what port to open for local application connections
SocksListenAddress 127.0.0.1 # accept connections only from localhost
#SocksListenAddress 192.168.0.1:9100 # listen on this IP:port also

## Entry policies to allow/deny SOCKS requests based on IP address.
## First entry that matches wins. If no SocksPolicy is set, we accept
## all (and only) requests from SocksListenAddress.
#SocksPolicy accept 192.168.0.0/16
#SocksPolicy reject *

## Logs go to stdout at level "notice" unless redirected by something
## else, like one of the below lines. You can have as many Log lines as
## you want.
##
## We advise using "notice" in most cases, since anything more verbose
## may provide sensitive information to an attacker who obtains the logs.
##
## Send all messages of level 'notice' or higher to /var/log/tor/notices.log
#Log notice file /var/log/tor/notices.log
## Send every possible message to /var/log/tor/debug.log
#Log debug file /var/log/tor/debug.log
## Use the system log instead of Tor's logfiles
#Log notice syslog
## To send all messages to stderr:
#Log debug stderr

## Uncomment this to start the process in the background... or use
## --runasdaemon 1 on the command line. This is ignored on Windows;
## see the FAQ entry if you want Tor to run as an NT service.
#RunAsDaemon 1

## The directory for keeping all the keys/etc. By default, we store
## things in $HOME/.tor on Unix, and in Application Data\tor on Windows.
#DataDirectory /var/lib/tor

## The port on which Tor will listen for local connections from Tor
## controller applications, as documented in control-spec.txt.
#ControlPort 9051
## If you enable the controlport, be sure to enable one of these
## authentication methods, to prevent attackers from accessing it.
#HashedControlPassword 16:872860B76453A77D60CA2BB8C1A7042072093276A3D701AD684053EC4C
#CookieAuthentication 1

############### This section is just for location-hidden services ###

## Once you have configured a hidden service, you can look at the
## contents of the file ".../hidden_service/hostname" for the address
## to tell people.
##
## HiddenServicePort x y:z says to redirect requests on port x to the
## address y:z.

#HiddenServiceDir /var/lib/tor/hidden_service/
#HiddenServicePort 80 127.0.0.1:80

#HiddenServiceDir /var/lib/tor/other_hidden_service/
#HiddenServicePort 80 127.0.0.1:80
#HiddenServicePort 22 127.0.0.1:22

################ This section is just for relays #####################
#
## See [https://www.torproject.org/docs/tor-doc-relay](https://www.torproject.org/docs/tor-doc-relay) for details.

## Required: what port to advertise for incoming Tor connections.
#ORPort 9001
## If you want to listen on a port other than the one advertised
## in ORPort (e.g. to advertise 443 but bind to 9090), uncomment the
## line below too. You'll need to do ipchains or other port forwarding
## yourself to make this work.
#ORListenAddress 0.0.0.0:9090

## A handle for your relay, so people don't have to refer to it by key.
#Nickname ididnteditheconfig

## The IP address or full DNS name for your relay. Leave commented out
## and Tor will guess.
#Address noname.example.com

## Define these to limit how much relayed traffic you will allow. Your
## own traffic is still unthrottled. Note that RelayBandwidthRate must
## be at least 20 KBytes.
#RelayBandwidthRate 100 KBytes  # Throttle traffic to 100KB/s (800Kbps)
#RelayBandwidthBurst 200 KBytes # But allow bursts up to 200KB/s (1600Kbps)

## Contact info to be published in the directory, so we can contact you
## if your relay is misconfigured or something else goes wrong. Google
## indexes this, so spammers might also collect it.
#ContactInfo Random Person <nobody AT example dot com>
## You might also include your PGP or GPG fingerprint if you have one:
#ContactInfo 1234D/FFFFFFFF Random Person <nobody AT example dot com>

## Uncomment this to mirror directory information for others. Please do
## if you have enough bandwidth.
#DirPort 9030 # what port to advertise for directory connections
## If you want to listen on a port other than the one advertised
## in DirPort (e.g. to advertise 80 but bind to 9091), uncomment the line
## below too. You'll need to do ipchains or other port forwarding yourself
## to make this work.
#DirListenAddress 0.0.0.0:9091
## Uncomment to return an arbitrary blob of html on your DirPort. Now you
## can explain what Tor is if anybody wonders why your IP address is
## contacting them. See contrib/tor-exit-notice.html for a sample.
#DirPortFrontPage /etc/tor/exit-notice.html

## Uncomment this if you run more than one Tor relay, and add the identity
## key fingerprint of each Tor relay you control, even if they're on
## different networks. You declare it here so Tor clients can avoid
## using more than one of your relays in a single circuit. See
## [https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#MultipleServers](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#MultipleServers)
#MyFamily $keyid,$keyid,...

## A comma-separated list of exit policies. They're considered first
## to last, and the first match wins. If you want to _replace_
## the default exit policy, end this with either a reject *:* or an
## accept *:*. Otherwise, you're _augmenting_ (prepending to) the
## default exit policy. Leave commented to just use the default, which is
## described in the man page or at
## [https://www.torproject.org/documentation.html](https://www.torproject.org/documentation.html)
##
## Look at [https://www.torproject.org/faq-abuse.html#TypicalAbuses](https://www.torproject.org/faq-abuse.html#TypicalAbuses)
## for issues you might encounter if you use the default exit policy.
##
## If certain IPs and ports are blocked externally, e.g. by your firewall,
## you should update your exit policy to reflect this -- otherwise Tor
## users will be told that those destinations are down.
##
#ExitPolicy accept *:6660-6667,reject *:* # allow irc ports but no more
#ExitPolicy accept *:119 # accept nntp as well as default exit policy
#ExitPolicy reject *:* # no exits allowed
#
## Bridge relays (or "bridges") are Tor relays that aren't listed in the
## main directory. Since there is no complete public list of them, even if an
## ISP is filtering connections to all the known Tor relays, they probably
## won't be able to block all the bridges. Also, websites won't treat you
## differently because they won't know you're running Tor. If you can
## be a real relay, please do; but if not, be a bridge!
#BridgeRelay 1
#ExitPolicy reject *:*

---

### Post by Cpierce on 2011-08-18
This solved it for me 

[http://ubuntuforums.org/showpost.php?p=9226418&postcount=3](http://ubuntuforums.org/showpost.php?p=9226418&postcount=3)

---

### Post by windeguy on 2011-08-18
I just checked the advanced settings in Vidalia, 

As Byrant suggested I did this


In the box labeled 'Tor Configuration File', change the default to '/etc/tor/torrc'.   

I put /etc/tor/torrc in and hit OK. 

However, when I go back to look at the Tor Configuration File box it is changed to: 

/home/mike/.vidalia/torrc

I took a look at that torrc file and it was blank.  I then copied the recommended torrc file into that blank file, but 
it did not help.  I still get the same error.

---

### Post by windeguy on 2011-08-18
> **Cpierce said:**
> This solved it for me 

[http://ubuntuforums.org/showpost.php?p=9226418&postcount=3](http://ubuntuforums.org/showpost.php?p=9226418&postcount=3)

The link you posted worked.  I did not have to Kill the tor process since it was not already running.  But the configuration program did show that Tor had some X's at other levels.  By installing the configuration program and removing those X's from Tor and rebooting my system I was able to start Vidalia and Tor is running. The details that I needed started with installing sysv-rc-conf since I did not need to kill tor: 

Turn off tor...

pidof tor
sudo kill <the pid of tor>

Install sysv-rc-conf...

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

scroll down with the arrow keys (alphabetical order) should look like...
tor          [ ]        [X]         [X]         [X]        [X]        [ ]        [ ]
scroll over the X's for tor and "unselect" them with the spacebar



Between Bryant and Cpierces suggestions, I think I have a working Vidalia/Tor. Now I just have to figure out how to best use it. Any advice on that is appreciated. Thanks!

---

### Post by windeguy on 2011-08-18
Now that Tor is up and running, I installed the Tor Button for Firefox and tried to use it. No luck.  It seems that Polipo is not running since I cannot see it in the Task Manager. On to the next phase of figuring out what is missing.  Any suggestions? Tor Button settings are set to use Polipo. 

I have searched for solutions to this problem. One site says privoxy is needed to run the tor button in Firefox, another site says that privoxy and polipo have conflict with each other.  

At the moment,  I am guessing there is a config file problem in polipo.  Here is the file at /etc/polipo$ 



### Basic configuration
### *******************

# Uncomment one of these if you want to allow remote clients to
# connect:

# proxyAddress = "::0"        # both IPv4 and IPv6
# proxyAddress = "0.0.0.0"    # IPv4 only

proxyAddress = "127.0.0.1"
proxyPort = 8117

# If you do that, you'll want to restrict the set of hosts allowed to
# connect:

# allowedClients = "127.0.0.1, 134.157.168.57"
# allowedClients = "127.0.0.1, 134.157.168.0/24"

allowedClients = 127.0.0.1
allowedPorts = 1-65535

# Uncomment this if you want your Polipo to identify itself by
# something else than the host name:

proxyName = "localhost"

# Uncomment this if there's only one user using this instance of Polipo:

cacheIsShared = false

# Uncomment this if you want to use a parent proxy:

# parentProxy = "squid.example.org:3128"

# Uncomment this if you want to use a parent SOCKS proxy:

socksParentProxy = localhost:9050
#socksProxyType = socks5


### Memory
### ******

# Uncomment this if you want Polipo to use a ridiculously small amount
# of memory (a hundred C-64 worth or so):

# chunkHighMark = 819200
# objectHighMark = 128

# Uncomment this if you've got plenty of memory:

# chunkHighMark = 50331648
# objectHighMark = 16384

chunkHighMark = 67108864

### On-disk data
### ************

# Uncomment this if you want to disable the on-disk cache:

diskCacheRoot = ""

# Uncomment this if you want to put the on-disk cache in a
# non-standard location:

diskCacheRoot = "~/.polipo-cache/"

# Uncomment this if you want to disable the local web server:

localDocumentRoot = ""

# Uncomment this if you want to enable the pages under /polipo/index?
# and /polipo/servers?.  This is a serious privacy leak if your proxy
# is shared.

# disableIndexing = false
# disableServersList = false

disableLocalInterface = true
disableConfiguration = true

### Domain Name System
### ******************

# Uncomment this if you want to contact IPv4 hosts only (and make DNS
# queries somewhat faster):
#
# dnsQueryIPv6 = no

# Uncomment this if you want Polipo to prefer IPv4 to IPv6 for
# double-stack hosts:
#
# dnsQueryIPv6 = reluctantly

# Uncomment this to disable Polipo's DNS resolver and use the system's
# default resolver instead.  If you do that, Polipo will freeze during
# every DNS query:

dnsUseGethostbyname = yes


### HTTP
### ****

# Uncomment this if you want to enable detection of proxy loops.
# This will cause your hostname (or whatever you put into proxyName
# above) to be included in every request:

disableVia = true

# Uncomment this if you want to slightly reduce the amount of
# information that you leak about yourself:

# censoredHeaders = from, accept-language
# censorReferer = maybe

censoredHeaders = from,accept-language,x-pad,link
censorReferer = maybe

# Uncomment this if you're paranoid.  This will break a lot of sites,
# though:

# censoredHeaders = set-cookie, cookie, cookie2, from, accept-language
# censorReferer = true

# Uncomment this if you want to use Poor Man's Multiplexing; increase
# the sizes if you're on a fast line.  They should each amount to a few
# seconds' worth of transfer; if pmmSize is small, you'll want
# pmmFirstSize to be larger.

# Note that PMM is somewhat unreliable.

# pmmFirstSize = 16384
# pmmSize = 8192

# Uncomment this if your user-agent does something reasonable with
# Warning headers (most don't):

# relaxTransparency = maybe

# Uncomment this if you never want to revalidate instances for which
# data is available (this is not a good idea):

# relaxTransparency = yes

# Uncomment this if you have no network:

# proxyOffline = yes

# Uncomment this if you want to avoid revalidating instances with a
# Vary header (this is not a good idea):

# mindlesslyCacheVary = true

# Suggestions from Incognito configuration
maxConnectionAge = 5m
maxConnectionRequests = 120
serverMaxSlots = 8
serverSlots = 2
tunnelAllowedPorts = 1-65535
# changed by Mike
disableLocalInterface=true

---

### Post by windeguy on 2011-08-18
I was able to get the Tor button to work by using this command:

sudo /etc/init.d/polipo/restart

What was missing was the correct setting in Vidalia to start polipo because there was nothing in the line under Settings/General:

"Start a proxy application when Tor starts"


I added **/etc/init.d/polipo** to the box for "Start a proxy application when Tor starts", checked the tick box so that Vidalia looks for the proxy and now the Tor button is working in Firefox.

---

### Post by Cpierce on 2011-08-18
So are you fixed ?

---

### Post by windeguy on 2011-08-19
> **Cpierce said:**
> So are you fixed ?

Yes thank you all for the suggestions. Vidalia, Tor the the Tor button in Firefox  are now working.

---

### Post by hkarn on 2011-08-29
Yes, TOR is already running. 

I have been getting around this by killing the tor process in the terminal before but I found an easy permanent solution now.

Install BootUp-Manager from software center. There you will find "anonymizing overlay network for TCP, tor" De-Activate apply.

Tor will not start until Vidalia asks for it now. If you want Vidalia to start automatically you can just add it in System settings, startup applications.




> **windeguy said:**
> Hello Bryant, 
Thank you for posting the information since I too have not had any luck getting TOR and Vidalia to work in Ubuntu 10.04.  One problem when I open Vidalia is taht it gives me an error message that TOR cannot connect because it thinks TOR is already running. TOR is not already running. Here is what Vidalia reports: 


---

