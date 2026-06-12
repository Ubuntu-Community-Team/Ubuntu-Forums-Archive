---
title: "vmware 2.0 server web interface always forever loading"
date: 2009-04-13
forum: Virtualisation
---

### Post by ubantuwannabe on 2009-04-13
Hi initially I tot there's something wrong with my guest os so i reinstall the guest os, i.e windows xp again in vmware server 2.0.

I was able to use it yesterday.

but right now whenever I type [https://127.0.0.1:8333/ui/](https://127.0.0.1:8333/ui/).

it always display Loading...... in the title only.

I have tail the following.

sudo /etc/init.d/vmware-mgmt start

as in in/bootstrap.jar:/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/bin/commons-logging-api.jar -Dcatalina.base=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16 -Dcatalina.home=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16 -Djava.io.tmpdir=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/temp org.apache.catalina.startup.Bootstrap start', failure limit reached
Apr 13 12:03:56 doordie-laptop NetworkManager: <debug> [1239595436.393016] wpa_parse_wpa_ie_wpa(): wpa_parse_wpa_ie_wpa: ie count botch (pairwise), count 0 left 6 
Apr 13 12:04:04 doordie-laptop NetworkManager: <debug> [1239595444.282000] wpa_parse_wpa_ie_wpa(): wpa_parse_wpa_ie_wpa: ie count botch (pairwise), count 0 left 6 
Apr 13 12:05:56 doordie-laptop NetworkManager: <debug> [1239595556.409527] wpa_parse_wpa_ie_wpa(): wpa_parse_wpa_ie_wpa: ie count botch (pairwise), count 0 left 6 
^Z
[1]+  Stopped                 tail -f /var/log/syslog

is there any one that could help me to resolve this forever loading vmware server 2.0 issues?

thanks

---

### Post by hyper_ch on 2009-04-13
not really a help but I never liked vmware server 2.0... that new interface always gave trouble to me and I think it uses much more systme resources. So for a long time I continued to use vmware server 1.0x before I changed now to workstation.

---

### Post by theDaveTheRave on 2009-04-14
Hi gents

I'm trying to get Vmware Server to work, and I have a "similar" problem to the OP.

When I try to log in to the [https://127.0.0.1:8222/ui/](https://127.0.0.1:8222/ui/). server everything seems to work OK but not when I go to the [https://127.0.0.1:8333/ui/](https://127.0.0.1:8333/ui/). server?

However I haven't been able to "install" a guest OS as yet, is this because i am using the [https://127.0.0.1:8222/ui/](https://127.0.0.1:8222/ui/). page?

Also I am trying to install a virutal Hardy system, I get to the Ubuntu logo, with the load bar, but then nothing?

Have I got a problem with my set up? or should I try the VMware server version 1 as hyper_ch suggests?

In case you are wondering why I want to virtualise ubuntu, most of my colleagues use either MAC, XP or Vista, but they wan't to use as much Open source stuff as possible. So to start with they would like to have things running on a Virtual system, so as they can hop in and out of the system as they please.

Also they want to have access to a copy of the database that I am developing, and it has been suggested that I should put this on the virtual system also, which makes sense, but I'm not sure how effective this will be. 

Any help / advice would be really appreciated, thanks in advance

David

---

### Post by ubantuwannabe on 2009-04-14
Hi all I did a remote login and add in the exception. it display the login page.

in summary

[https://127.0.0.1/8333/ui/](https://127.0.0.1/8333/ui/) not able to display login

[https://localhost:8333/ui/#](https://localhost:8333/ui/#) able to display login

[https://192.168.1.102:8333/ui/#](https://192.168.1.102:8333/ui/#) able to display login

could anyway tell me what is wrong with 
[https://127.0.0.1/8333/ui/](https://127.0.0.1/8333/ui/) not being able to display? thanks

---

### Post by Dedoimedo on 2009-04-14
What does your /etc/hosts file look like?
Question two, are you using any sort of a firewall?

Dedoimedo

---

### Post by ubantuwannabe on 2009-04-14
127.0.0.1	localhost
127.0.1.1	doordie-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

thanks

---

### Post by fduff on 2009-04-14
have a look here: [http://ubuntuforums.org/showthread.php?t=953319](http://ubuntuforums.org/showthread.php?t=953319)

Duff

---

### Post by Dedoimedo on 2009-04-14
ubantu, did you edit those manually?

Try creating a single entry:

127.0.0.1 localhost localhost.localdomain doordie-laptop

Remove the other two 127.

See if this helps. Naturally, back the original one first!

Cheers,
Dedoimedo

---

### Post by ubantuwannabe on 2009-04-15
Hi all,

I've stop and start vmware server 2.0  and here's the investigation

doordie@doordie-laptop:~$ sudo service vmware start
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual machine communication interface                             done
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                         failed

my NAT seems to have failed.

---

### Post by x-lin on 2009-06-15
Hi all, here's a strange one:

I experienced exactly the same annoying problem. After having removed directory .mozilla from my home directory, it worked until I applied a new theme to Firefox. Then the "loading..." screen was there again. After I had reset to the Firefox default theme, vmware server console loads immediately.

Hope someone will be helped by this

---

### Post by HermanAB on 2009-06-16
The real solution is to upgrade VMware 2.x to 1.x.

The 2.x version is best avoided.

---

### Post by malyvelky on 2009-07-20
I too experienced the problem, accessing [https://localhost:8333/ui/](https://localhost:8333/ui/) using Konqueror revealed that javascript has a variable undefined, which would indicate that the javascript that defines it loads later than it should.

After some experiments the vmware console suddenly loaded without problems in all browser I have. So maybe some temporary runtime condition of the server changed.

Since this looks as a random problem I'd recommend to try to reload (Control-Shift-R in Firefox) the page several times.

---

### Post by bodhi.zazen on 2009-07-20
I too find vmware server 2.x is unreliable. I keep hoping they will improve the product, to comp0ete with KVM and VBox, but it seems vmware has no interest.

---

### Post by HermanAB on 2009-07-20
Howdy,

Vmware 2.0 should not be lightly discarded.  It should be thrown, with great force...

You should upgrade to the 1.x series, Vmware Workstation or even Vmware player.  Otherwise, give up and install Virtualbox.

Vmware 2.0 reminds me of Windows Vista and is best avoided.

---

### Post by jchatham on 2009-11-17
I saw the same situation as x-lin -- all I had to do was rm -rf .mozilla/firefox/*/Chrome, and poof - no more issues.

Of course, I've also done a few other hacks to make vmware server two a bit less flaky - for one thing, you can edit /etc/init.d/vmware to make it use, for example, sun java 1.6 for the webAccess executable, instead of its own bundled version of java.  Giving the webAccess process more memory (and removing the -XXwhatever memory management options) also seemed to help.
Oh, and then there's the [vmware-hostd LD_LIBRARY_PATH tinkering]("http://communities.vmware.com/thread/242151?tstart=15") you need to do to make it reliable on ubuntu 9.10.

That all said - I can certainly see where HermanAB is coming from.  And, for personal use, I would not recommend vmware server two; the web UI is just poorly designed.  However, if you need to be able to automate the thing, vmware server two lets you use the [vijava api]("http://vijava.sourceforge.net/"), which (at least in my experience) is far cleaner and more stable than the vix api you're stuck with on vmware server one.  And, for my purposes, that's reason enough to use server two over server one.

---

