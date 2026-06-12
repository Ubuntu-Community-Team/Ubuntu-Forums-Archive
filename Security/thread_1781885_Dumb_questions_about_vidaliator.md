---
title: "Dumb questions about vidalia/tor"
date: 2011-06-14
forum: Security
---

### Post by sandman887 on 2011-06-14
I have vidalia/tor running (or at least it appears to be running) however, from the conf file that was suggested for polipo, I'm not sure, but it seems it sets parameters to allow remote clients to connect. Does that mean they can connect to my computer? If so, how does that make you more secure when you're using the tor network? 

Also, when I clicked on view network, it showed names. Are those usernames of connected Tor users? If so, once again, if you can be seen on the Tor network, how does that help your anonymity?

Finally, what is this create identity thing? 

I have checked Tor's documentation, and googled, and was unable to find these answers. Sorry for the stupid questions, however, I was unable to find any relevant subject titles when I was searching through their documentation.

This is the code from the file build-scripts_config_polipo.conf


```
### Basic configuration
### *******************

# Uncomment one of these if you want to allow remote clients to
# connect:

# proxyAddress = "::0"        # both IPv4 and IPv6
# proxyAddress = "0.0.0.0"    # IPv4 only

proxyAddress = "127.0.0.1"
proxyPort = 8118

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

socksParentProxy = "localhost:9050"
socksProxyType = socks5


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

# diskCacheRoot = "~/.polipo-cache/"

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
```

---

### Post by handy on 2011-06-14
You may have more of a chance of getting some help if you make a post where you have pasted in the text that you are having trouble with.

Tor is a terrific tool for protecting our surfing privacy, though as they themselves state, it is not perfect.

I think that you are misunderstanding some of the info' that you have been reading, or are "perhaps" reading info' relating to setting up a Tor node, where you supply bandwidth for people to be routed through your machine. That is not the way most people use Tor. Though if there were more routers (nodes) it would be quicker & more effective than it is.

---

