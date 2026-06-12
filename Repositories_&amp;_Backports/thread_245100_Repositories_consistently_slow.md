---
title: "Repositories consistently slow"
date: 2006-08-27
forum: Repositories &amp; Backports
---

### Post by pomegranate on 2006-08-27
I've been having more or less constant problems getting updates and programs from the repositories since I installed Drake a month ago. I've done a lot of fiddling around with sources.list and using different people's recommended lists and the default list with different local mirrors. All the same, apt-get update and the package manager always have the same problem - downloads are ridiculously slow, to the point that anything over a few hundred bytes is automatically given up on, and the package status ends up being 'Failed'. My download speed ranges from 'unknown' to something like 300 Bps.
So:
Can someone confirm what repositories are actually working properly, and what speed I should expect from a functional rep source?
Is there anywhere that keeps a report on the status of the repositories and various mirrors. 

Here is my current sources.list, with which I'm experiencing the problem I explain above.


> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse


Please help.

---

### Post by Benjamin_Lebsanft on 2006-08-27
I'm experiencing the same, although my speed sometimes reaches 22kB/s ;)

---

### Post by pomegranate on 2006-08-27
Also, I keep getting this message:
"Errhttp://security.ubuntu.com dapper-security/main Packages
  Sub-process gzip returned an error code (1)"

when doing apt-get update, which I don't think I had until recently. And this is with a clean sources.list...

---

### Post by pomegranate on 2006-08-27
Anyone help? These are very simple questions I'm asking, I understand that much.

---

### Post by Anonii on 2006-08-28
> **pomegranate said:**
> Anyone help? These are very simple questions I'm asking, I understand that much.



I guess you can use browsers, like Firefox etc, with a normal speed, right?

A little extreme, but:
Are you using any anonymity tools like tor, or privoxy?
Is there something like 
> http_proxy=http://127.0.0.1:8118/
HTTP_PROXY=$http_proxy
export http_proxy HTTP_PROXY
in your ~/.bashrc?

---

### Post by jdong on 2006-08-28
Are you able to get online and browse the web and download from elsewhere at normal speeds? What you're describing seems to be a strange network problem.

---

### Post by jdong on 2006-08-28
At the moment, you're not the only one having issues with the archive.ubuntu.com servers -- they are going at like 20KB/s for me and others in the IRC channels. I'm sure they're working on resolving whatever network issues they're having.

---

### Post by pomegranate on 2006-08-28
> **Anonii said:**
> I guess you can use browsers, like Firefox etc, with a normal speed, right?

Right

> **Anonii said:**
> A little extreme, but:
Are you using any anonymity tools like tor, or privoxy?

Not to my knowledge. I've certainly not knowingly installed anything of the sort.

> **Anonii said:**
> Is there something like 

in your ~/.bashrc?

I've not encountered bashrc before, the contents of my etc/bash.bashrc are below, is that the file you mean? 
> # System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi



> **jdong said:**
> Are you able to get online and browse the web and download from elsewhere at normal speeds? What you're describing seems to be a strange network problem.

Yeah I've no problems with the net otherwise, and get speeds of 200kbps from my music service site.
Yes, some form of network configuration oddness on my side is all I can think of, but I've no idea where to start to address it. I've tried using both my wireless connection and ethernet, with identical results.

> **jdong said:**
> At the moment, you're not the only one having issues with the archive.ubuntu.com servers -- they are going at like 20KB/s for me and others in the IRC channels. I'm sure they're working on resolving whatever network issues they're having.

I've been aware that there's been problems with the servers, but that seems to have been the case for a month now, and I assumed it must have been resolved by now and that the problem was on my side. That's why I'm asking about what speeds people get from the servers, and what speeds are the norm. Are there any mirrors that give better speeds? I've tried changing to .gb/uk .fr, .br. and .ca without any obvious improvement.


Thanks for your assistance so far, chaps.

---

### Post by jdong on 2006-08-28
Well, to satisfy your curiousity, on a normal basis I get 150-200KB/s from Ubuntu's archive.ubuntu.com, while my connection is capable of around 550KB/s.

Today, I've been down around 20-30KB/s, too, and at times stalls.


I really don't know what to tell you at the moment, other than let's sit and wait a bit for the situation to settle, and see if the problem still persists.

If it's been like this for a month for you, then I'd be tempted to blame your ISP or something else about your network configuration

---

### Post by pomegranate on 2006-08-28
I did get decent speeds on ONE occasion... not sure what happened after that though :(

---

### Post by shunthemask on 2006-08-28
Have you tried doing a traceroute to see if there is anything funky going on with your isp?  I've seen problems similar to this before where the traffic bounces from the east coast to the west coast just to get to a server on the east coast.

---

### Post by pomegranate on 2006-08-28
Can you tell me how to do that? Bare in mind I'm in UK, not the States...

---

### Post by shunthemask on 2006-08-28
well, it seems that ubuntu doesn't install traceroute by default, so you have to:
```
sudo apt-get install traceroute
```

and to run, just type in 
```
traceroute <hostname>
```
where <hostname> is the hostname of the repo that you are trying to access.  Then stick the output up here and we'll take a look at it.

---

### Post by pomegranate on 2006-08-28
when typing
> sudo apt-get install traceroute
I get:
> Reading package lists... Done
Building dependency tree... Done
Package traceroute is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package traceroute has no installation candidate

??

---

### Post by shunthemask on 2006-08-28
I must have a repo in my list that you don't have (and I thought that it was hilarious that traceroute doesn't come with the standard install).  You can try tracepath instead:
```
tracepath <hostname>
```
and if you don't have this bad boy installed:
```
sudo apt-get install iputils-tracepath
```
Synaptic says "the tracepath utility is similar to the traceroute utility, but also attempts to discover the MTU of the path".

---

### Post by jdong on 2006-08-28
> **shunthemask said:**
> (and I thought that it was hilarious that traceroute doesn't come with the standard install).

Because tracepath comes in the standard install and was a better alternative than traceroute?

---

### Post by pomegranate on 2006-08-28
did tracepath, got this:
>  tracepath ubuntu.com
 1:  192.168.1.2 (192.168.1.2)                              0.177ms pmtu 1500
 1:  mygateway.ar7 (192.168.1.1)                            7.094ms
 2:  brhm-bam-2.inet.ntl.com (194.145.148.3)               57.981ms
 3:  brhm-t2core-a-ge-wan74.inet.ntl.com (213.106.231.85)  59.579ms
 4:  bir-bb-a-so-700-0.inet.ntl.com (213.105.174.105)      57.886ms
 5:  man-bb-b-so-700-0.inet.ntl.com (62.253.185.134)       61.920ms
 6:  man-bb-a-ae0-0.inet.ntl.com (62.253.187.177)         asymm  7  59.380ms
 7:  212.187.137.1 (212.187.137.1)                         60.640ms
 8:  so-4-1-0.mp1.manchesteruk1.level3.net (4.68.113.101) asymm  9  61.658ms
 9:  ae-1-0.bbr1.london2.level3.net (212.187.128.46)      asymm 10  91.367ms
10:  ae-0-53.gar1.london2.level3.net (4.68.117.75)        asymm  9  65.441ms
11:  ge-6-2.core-r-1.lon2.mnet.net.uk (195.50.91.138)     asymm  9  69.344ms
12:  vlan102.core-l-1.lon2.mnet.net.uk (62.140.218.201)   asymm 10  66.142ms
13:  85.133.32.130 (85.133.32.130)                        asymm 11  65.749ms
14:  82.211.81.76 (82.211.81.76)                          asymm 12  70.028ms
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500

---

### Post by jdong on 2006-08-28
Your tracepath looks normal to ubuntu.com -- at hop 14 the router begins blocking pings. Can you check your tracepath to **archive.ubuntu.com**? It's a different server.

---

### Post by pomegranate on 2006-08-28
ok

> tracepath archive.ubuntu.com
 1:  192.168.1.2 (192.168.1.2)                              0.279ms pmtu 1500
 1:  mygateway.ar7 (192.168.1.1)                            2.709ms
 2:  brhm-bam-2.inet.ntl.com (194.145.148.3)               56.491ms
 3:  brhm-t2core-a-ge-wan74.inet.ntl.com (213.106.231.85)  56.839ms
 4:  bir-bb-a-so-700-0.inet.ntl.com (213.105.174.105)      60.169ms
 5:  bir-bb-b-ae0-0.inet.ntl.com (62.253.185.154)         asymm  4  58.917ms
 6:  nth-bb-a-so-300-0.inet.ntl.com (62.253.185.105)      asymm  5  60.595ms
 7:  fran-ic-1-as0-0.inet.ntl.com (213.105.174.86)        asymm 11  77.631ms
 8:  decix.mpd01.fra03.atlas.cogentco.com (80.81.192.63)  asymm 11  78.380ms
 9:  te3-4.mpd01.ams03.atlas.cogentco.com (130.117.1.162) asymm 12  86.771ms
10:  p9-0.core02.jfk02.atlas.cogentco.com (130.117.1.170) asymm 13  94.017ms
11:  t3-3.mpd01.lon01.atlas.cogentco.com (130.117.2.25)   asymm 14  93.505ms
12:  149.6.81.211 (149.6.81.211)                          asymm 15  91.728ms
13:  archive.ubuntu.com (195.248.90.54)                   asymm 16  97.261ms reached
     Resume: pmtu 1500 hops 13 back 16
tom@tom-ubuntu:~$


---

### Post by shunthemask on 2006-08-28
Hmm, i don't know what your problem is, but I know what it isn't.  You're much closer to the repos and I get good speed:
```
r00t@nyquil:~$ tracepath archive.ubuntu.com
 1:  192.168.0.2 (192.168.0.2)                              0.245ms pmtu 1492
 1:  no reply
 2:  ge-2-2-ur01.bayville.nj.panjde.comcast.net (68.86.221.29)  17.081ms
 3:  te-1-1-ur01.dover.nj.panjde.comcast.net (68.86.210.58)  18.063ms
 4:  te-1-1-ur02.dover.nj.panjde.comcast.net (68.86.210.62)  38.352ms
 5:  te-1-1-ur01.brick2.nj.panjde.comcast.net (68.86.210.66)  22.426ms
 6:  te-1-1-ur01.brick1.nj.panjde.comcast.net (68.86.210.70)  17.655ms
 7:  te-1-1-ur01.eatontown.nj.panjde.comcast.net (68.86.210.74)  59.027ms
 8:  te-1-1-ur02.eatontown.nj.panjde.comcast.net (68.86.210.78)  42.276ms
 9:  te-2-1-ar01.eatontown.nj.panjde.comcast.net (68.86.210.82)  97.606ms
10:  po-10-ar01.absecon.nj.panjde.comcast.net (68.86.208.18)  48.555ms
11:  po-10-ar01.audubon.nj.panjde.comcast.net (68.86.208.22)  23.299ms
12:  ge-3-0-cr01.turnersville.nj.core.comcast.net (68.86.211.10)  46.352ms
13:  12.118.114.13 (12.118.114.13)                        asymm 14  24.792ms
14:  no reply
15:  no reply
16:  12.122.80.57 (12.122.80.57)                          asymm 17  47.268ms
17:  att-gw.dc.cogent.net (192.205.32.86)                 asymm 18  42.389ms
18:  v3493.mpd01.iad01.atlas.cogentco.com (154.54.5.38)   asymm 19  45.091ms
19:  v3494.mpd01.dca01.atlas.cogentco.com (154.54.5.41)   asymm 20 139.107ms
20:  t7-2.mpd03.jfk02.atlas.cogentco.com (154.54.5.245)   asymm 21 141.683ms
21:  g13-0-0.core02.jfk02.atlas.cogentco.com (154.54.5.233) asymm 22 106.101ms
22:  p14-0.core01.lon01.atlas.cogentco.com (66.28.4.254)  asymm 23 141.664ms
23:  ten3-1.mpd01.lon01.atlas.cogentco.com (130.117.1.62) 199.485ms
24:  149.6.81.211 (149.6.81.211)                          176.796ms
25:  195.248.90.54 (195.248.90.54)                        220.363ms reached
     Resume: pmtu 1492 hops 25 back 25

```

---

### Post by shunthemask on 2006-08-28
> **jdong said:**
> Because tracepath comes in the standard install and was a better alternative than traceroute?

not really, just set in my ways, I guess.  I have been using traceroute since the beginning of time and I am not used to a system that doesn't have it installed by default.  (And I am a retard and didn't know whether tracepath was installed by default.)

---

### Post by pomegranate on 2006-08-29
can you post your sources.list so I can try it?

---

### Post by jdong on 2006-08-29
in #ubuntu-devel tonight (the developer's IRC chat room):

> [21:24] <jdong> I'd like to take this moment to complain a bit about why archive.ubuntu.com is so slow?
[21:25] <jdong> 5-20kb/s
[21:25] <Burgundavia> jdong: the DC in london is having issue, afaik


So, it seems like it's a network issue at Canonical's side. Downloads continue to crawl at 10-20KB/s for me, sometimes dipping lower. Many of the country codes probably still point back to the master mirror following the xorg disaster a week back.... so that might explain why a lot of mirrors are slow.

---

### Post by pomegranate on 2006-08-31
Any further suggestions as to what is going on? 
I'm still getting download speeds of < 1kbps.

---

### Post by gruntu on 2006-09-05
IT IS STILL SLOW. You know I wouldn't mind slow (35k for me) if the connection didn't drop out before the image completed its download. And no it's not my provider because I have other downloads running at the same time and the don't drop out.

I tried other mirrors around the world with the same results. My trace routes never go over 100ms to the repositories.:(

---

### Post by jdong on 2006-09-05
Hmm, my connection to archive.ubuntu.com is more or less normal-speed now, hovering around 400KB/s.

---

### Post by gruntu on 2006-09-06
I checked it again after your reply and it is much improved. Thanks for fixing it. It's not nearly as fast as it used to be but I know Ubuntu is getting very popular.

Thanks again:D

---

### Post by jdong on 2006-09-06
Well, I have no idea who fixed it, bu if it's improved that's all that matters. Even as Ubuntu gets more popular, its mirrors should hold up, and for me that's stayed mostly true.


I still suspect there's some sort of connection problem from you guys to the Canonical servers, and that's causing your slow speeds, because even on release day, archive.ubuntu.com still pumps out broadband speeds for me.

---

### Post by kalpik on 2006-09-30
archive.ubuntu.com *very* slow here too (7-8 KBps)

Tracepath:
```

kalpik@kalpik-desktop:~$ tracepath archive.ubuntu.com
 1:  192.168.1.33 (192.168.1.33)                            0.170ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              1.208ms
 2:  192.168.1.1 (192.168.1.1)                            asymm  1   7.932ms pmtu 1492
 3:  rasBTNLDel-static-230.215.56.202.mantraonline.com (202.56.215.230)  77.290ms
 4:  rasBTNLDel-static-162.215.56.202.mantraonline.com (202.56.215.162)  82.183ms
 5:  203.101.95.181 (203.101.95.181)                      asymm 10 117.474ms
 6:  203.101.100.181 (203.101.100.181)                    asymm 10 115.793ms
 7:  203.101.95.173 (203.101.95.173)                      asymm  9 126.123ms
 8:  61.95.180.11 (61.95.180.11)                          asymm  7 120.421ms
 9:  202.56.223.9 (202.56.223.9)                          asymm  8 116.231ms
10:  203.208.168.157 (203.208.168.157)                    asymm 16 351.582ms
11:  203.208.149.25 (203.208.149.25)                      asymm 14 348.855ms
12:  203.208.169.14 (203.208.169.14)                      asymm 14 626.478ms
13:  p9-0.core02.sfo01.atlas.cogentco.com (66.28.4.233)   asymm 14 634.648ms
14:  p4-0.core01.mci01.atlas.cogentco.com (66.28.4.210)   432.026ms
15:  p5-0.core02.ord01.atlas.cogentco.com (66.28.4.34)    asymm 14 426.626ms
16:  p15-0.core01.ord01.atlas.cogentco.com (66.28.4.61)   asymm 14 432.575ms
17:  p14-0.core01.bos01.atlas.cogentco.com (66.28.4.109)  asymm 14 425.594ms
18:  p3-0.core01.lon01.atlas.cogentco.com (130.117.0.45)  asymm 13 508.217ms
19:  ten3-1.mpd01.lon01.atlas.cogentco.com (130.117.1.62) asymm 14 501.585ms
20:  149.6.81.211 (149.6.81.211)                          asymm 13 490.720ms
21:  195.248.90.54 (195.248.90.54)                        asymm 14 517.144ms reached
     Resume: pmtu 1492 hops 21 back 14

```

---

### Post by CapnCook on 2006-10-08
they are slow as an old dog on a cold day here also.

---

### Post by kalpik on 2006-10-26
Umm.. Repos *still* slow here! I get a packet loss of around 50%!

---

### Post by jdong on 2006-10-26
Today it's gonna be pretty rough due to the Edgy release... I'm getting timeouts right now.

---

### Post by londonhelper on 2006-10-26
how long you think it will last?

---

### Post by Ammit on 2006-10-26
My upgrade from 6.06 to 6.10 is estimated to be completed in 10 hours. This is nuts ](*,)

---

### Post by kalpik on 2006-11-05
archive.ubuntu.com STILL slow (get only about 4-5KBps with it). Im really irritated with this now! Any idea if at all this will get resolved?

---

### Post by kreuters on 2006-11-11
i had the same problem with the gb repositories, switch to de.archive.ubuntu.com, getting 2000 Kb/s now.

---

### Post by kalpik on 2006-11-13
^^ Thanks a LOT for that tip! Im also getting full speeds with de.archive.ubuntu.com!

---

### Post by savohead on 2006-11-14
i know i could sound weird, but in a way you should be happy, this means MORE AND MORE people are installing Ubuntu and working with it!!! eheh ... sorry for my stupid post, i'll update to Edgy tomorrow and i'll see if i'll have this problem too

---

