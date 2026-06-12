---
title: "New Firewall Script For Ubuntu"
date: 2005-07-18
forum: Server Platforms
---

### Post by robert_pectol on 2005-07-18
I've written a stateful firewall script for Ubuntu Linux that is very easy to configure and install.  It automatically detects your IP, Network, Netmask, Gateway, etc.  It has support for many of the more common servers.  Others can easily be added as well.  There's also a simple init script for having it load upon booting your system.

At the moment, it is designed to protect a single workstation but future enhancements will provide many more features such as NAT routing, port forwarding, etc.  Although it's sorta still in, "beta" at the moment, it's fully functional and ready for others to try out.  I'm looking for comments/feedback/suggestions.  I'd like it to evolve based on inputs from the Ubuntu community.  I hope some find it useful and I hope to hear some comments.

To get a copy to try out on your system, go here:
[http://rob.pectol.com/content/view/2/1/](http://rob.pectol.com/content/view/2/1/)

*** Edited August 4, 2005 ***
The firewall now includes many of the suggestions and enhancements mentioned in the following posts!  If you have trouble corroborating comments in this thread with the firewall script, keep in mind that it has evolved substantially since it was first posted.  Although some of the following comments may not apply to the current revision of the firewall, they did indeed apply to the original hence the numerous changes!  I feel that this firewall is now very functional and should provide you with more than adequate protection for your Ubuntu box.  Give it a try and let me know what you think!

---

### Post by LordHunter317 on 2005-07-18
Your script has several issues, but I don't have time to cover them now.  I'll try to later tonite.

Problem one is the whole thing is too complicated, and tries to do things other parts of the system are responsible for.

Problem two is the firewall policy is too complicated.

---

### Post by robert_pectol on 2005-07-18
Cool!  Thanks for looking it over!  I'll anxiously await your observations...

---

### Post by skyboy on 2005-07-19
Wooa, I agree with you LordHunter, way to complicated for me :)
Just as an example and this doesnt pretend to be the top most solution, here is my iptables.sh, and it won't take much time :)
Basically, I allow SSH server connection, http server connection, file sharing and remote desktop control when I feel like :)
everything else  is dropped

#########iptables.sh###########################
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT
#sudo iptables -A INPUT -p tcp --dport 5900 -j ACCEPT 
#sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT
sudo iptables -A INPUT -p udp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT
sudo iptables -A OUTPUT -p udp -m multiport --destination-ports 445,135,136,137,138,139 -j ACCEPT
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -j DROP
#####################################

maybe there are ways to make it better but at least it's simple and understandable by human beings :D
If really mine sucks, then I'll try something more complicated :D

Sorry Robert, you've done great job anyway

---

### Post by dataw0lf on 2005-07-19
I think the script looks fine, Robert.  Firewalls, yes, can be complicated (especially iptables, which are considered rather estoretic knowledge).  

Here's a quick, cool hack for those of you interested in iptables:

```
iptables -N randomdrop
iptables -A randomdrop -m random --average 50 -j DROP
iptables -A randomdrop -j REJECT
``` 

This can be used anywhere where you'd usually DROP and/or REJECT packets.  What it does, in essence, is randomly split it's reaction to packets: 50% of the time it'll REJECT em, the other half of the time it'll DROP em.  This will confuse the hell out of your port scanning, wannabe hax0rz.

---

### Post by LordHunter317 on 2005-07-19
Ok, my apologies for not answer eariler, my evening was stolen from me by a tower climb.  I'm gracious you didn't take offensse to my troll and run.  I'm going to hilight the problems, but not go into super-detailed solutions.  If you help fixing anything or want my detailed suggestions, just ask and I'll be happy to provide them.

Ok, here we go :)[list][*]All of the configuration settings, like EXTIF, and ALLOW_HTTP, should go in a file in /etc/defaults in Debian/Ubuntu and /etc/sysconfig on RH and derivatives.  The file can be plain shell script, and you source it at script load similar to this:```
if [ -f /etc/default/firewall ] ; then
    . /etc/default/firewall
else
    echo "Could not load script configuration, firewall not configured..."
    exit 1
fi
```[*]Don't bother with a root test.  If you insist on doing one, then just exit silently.  The script is principally meant to be run by init at boot time, so it's safe to assume you're root and error out with tons of errors if the user is not.  It's standard practice and all the other scripts do it, so there's no reason for you not to.[*]The test for legal startup arguments is silly, because a properly written case statement will handle this automatically.  You should write the actions that need to happen for each startup argument in a function, then have a skeleton like so at the end of your script:```
case "$1" in
    start)
         do_start
    ;;
    stop)
          do_stop
    ;;
    restart)
          do_stop
          do_start
     ;;
    *)
          echo "Usage: /etc/init.d/firewall start|stop|restart"
          exit 0
    ;;
esac
```Which handles the checking and response to the provided argument.[*]Logging all traffic is somewhat silly, so I would take the code out.  It's your call, though.  The section that does that definitely needs to be moved to a startup function, though.[*]When you do interface detection, you shouldn't announce the operating system to the user.  They already know.[*]You shouldn't wait for the interface to come up on a DHCP system.  If the networking script doesn't already have a wait period in it, that's a bug.  If no IP address is on the interface, simply error out.  Your script shouldn't try to make up for other's shortcomings like that.[*]You shouldn't output the discovered IP address and such.  Init scripts should be totally silent, except for success, fail, or error.  If you really want to give them a way to do that, then have a verbose option they can set that will print the message if needed.[*]Of the modules you load, only loading ip_conntrack_ftp is necessary (and it's not necessary if ip_nat_ftp is loaded instead).  If the system can't automatically load dependent modules, it has more serious issues than a working firewall.[*]Shorten your iptables not found message to something like: "Iptables executable not found, exiting."[*]Clean up your status output.  All that extra spacing isn't needed.[*]It's not your job to play with ip_foward, tcp_syncookies, or rp_filter.  So don't.  On Debian and Ubuntu, that's the job of the main networking script.  All the other sysctls you set you should have options to allow the user to control whether they get set or not.[*]When  you lock down the firewall, setting DROP policies on the chains in the nat and mangle tables is unnecessary.  Merely flushing the rules and setting DROP policy on INPUT, OUTPUT, and FORWARD on the filter table will stop all traffic from traversing the system.[*]Doing egress filtering (the OUTPUT chain) is of debatable value normally and I recommend you don't do it.  You don't do any actual filtering, so I don't see the point of it at all, unless you enhance the rules.[*]> ```
$IPT -A INPUT  -m state --state INVALID -j DROP
$IPT -A OUTPUT  -m state --state INVALID -j DROP
```If your firewall is written correctly, these aren't needed.[*]> ```
#  Protection from stealth scans
# Clear all state flag bits
$IPT -A INPUT -p tcp --tcp-flags ALL NONE -j DROP
# Drop if the SYN and FIN bits are both set
$IPT -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP
# Drop if the SYN and RST bits are both set
$IPT -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j DROP
# Drop if the FIN and RST bits are both set
$IPT -A INPUT -p tcp --tcp-flags FIN,RST FIN,RST -j DROP
# Drop if the FIN bit is set without the expected accompanying ACK bit
$IPT -A INPUT -p tcp --tcp-flags ACK,FIN FIN -j DROP
# Drop if the PSH bit is set without the expected accompanying ACK bit
$IPT -A INPUT -p tcp --tcp-flags ACK,PSH PSH -j DROP
# Drop if the URG bit is set without the expected accompanying ACK bit
$IPT -A INPUT -p tcp --tcp-flags ACK,URG URG -j DROP
```All of this is unncessary, assuming your rules only allow in the proper starting traffic to begin with.  The kernel will throw out packets that are ill-formed without help of the firewall.  Writing rules to explictly  block them is rather silly.[*]> ```
# Drop malformed broadcast packets
$IPT -A INPUT -i $EXTIF -s $BCAST_DST -j DROP
$IPT -A INPUT -i $EXTIF -d $BCAST_DST -j DROP
$IPT -A INPUT -i $EXTIF -d $BCAST_SRC -j DROP
```The second rule of these three will break some DHCP applications, and possibly some SNMP ones as well.  Should definetely be configurable behavior.  Also, there's no need to use variables here for the network addresses.  In fact, any time you use a variable just once and aren't going to use it anywhere else, just hardcode the thing.  It'll make your script more readable[*]> ```
# Drop fragmented ICMP packets
$IPT -A INPUT --fragment -p icmp -j LOG --log-prefix "Fragmented ICMP: "
$IPT -A INPUT --fragment -p icmp -j DROP
```I question the value of this.  While fragmented ICMP packets are likely someone up to no good, they could still conceptually happen.  Moreover, this won't stop a ping flood, or other types of ICMP attacks anyway.  Plus, you'll have to do it before the state tracking.[*]> ```
# Allow DNS queries from this machine out ANY interface (and responses back in)
$IPT -A INPUT -p udp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT
```This rule is unnecessary. The global state tracking rule would have already got this traffic.[*]> ```
#  Necessary ICMP traffic
$IPT -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT

$IPT -A OUTPUT -p icmp --icmp-type source-quench -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type source-quench -j ACCEPT                       # Source Quench control type ICMP (type 4)

$IPT -A OUTPUT -p icmp --icmp-type parameter-problem -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type parameter-problem -j ACCEPT                   # Parameter Problem Status ICMP (type 12)

$IPT -A OUTPUT -p icmp --icmp-type fragmentation-needed -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type fragmentation-needed -j ACCEPT                # Destination Unreachable ICMP (type 3)

$IPT -A OUTPUT -p icmp --icmp-type time-exceeded -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type time-exceeded -j ACCEPT                       # Time Exceeded Status (type 11)
```All of this is unneccesary, once again, handled by state tracking.[*]> ```
ALLOW_SSHD" = "1" ]; then
	$IPT -A INPUT -i $EXTIF -p tcp --sport $UNPRIVPORTS -d $EXTIP --dport $SSHD_PORT -m state --state NEW -j ACCEPT
	$IPT -A INPUT -i $EXTIF -p tcp --sport $UNPRIVPORTS -d $EXTIP --dport $SSHD_PORT -j ACCEPT
```Hardcode the port **name**, don't use a variable (do this everywhere).  Don't bother looking at the incoming port, it doesn't mean anything in this case.  You're filtering out legal traffic.  Add '--syn' to the first rule.  Your second rule is unnecessary and shouldn't even get triggered anyway.  Remove it.[/list]That's most of it, I think.

---

### Post by robert_pectol on 2005-07-19
Thanks for the inputs everyone!  I'll be making some changes to it.  There were some pretty good suggestions as well as some with which I differ (mostly just personal preferences on some of them).  Firewall philosophy/methodology is indeed a vast subject and I certainely don't claim to be an expert!  Therefore, I happily accept all the criticisms and will use them to further "tune" the script.

I'll post back to this thread when I have made some changes to it.  Again, I'll be seeking comments, criticisms, suggestions, etc.  Thanks again all!

---

### Post by asimon on 2005-07-21
[QUOTE=dataw0lf]Here's a quick, cool hack for those of you interested in iptables:

```
iptables -N randomdrop
iptables -A randomdrop -m random --average 50 -j DROP
iptables -A randomdrop -j REJECT
``` 
[/QUOTE]
This looks very much like security by obscurity, doesn't it?

---

### Post by robert_pectol on 2005-07-21
Ok... the next revision is out and I've made some big changes to the script. It is now smaller and more functional (I believe) than it was before. I've removed some of the un-necessary bloat and complexity. It still does distro and IP address detection but is much less "kludgy" in how it does it. Also, since I'm writing this script specifically for Debian and Debian-derived systems, I've removed the script's attempt to continue "blindly" loading as if it were being run from a Red Hat or Mandrake system. Now it merely exits. I might add the ability to properly detect and support other distros down the road but for now, I'd first like to solidify the guts of the firewall with the help of the Ubuntu community.

So, with all that said, I present my new version.  You can get it at:
[http://rob.pectol.com/content/view/2/1/](http://rob.pectol.com/content/view/2/1/)

In response to the great number of criticisms and suggestions earlier in this thread, I offer the following explanations:

My reasoning for not putting the script variables in /etc/defaults was simply for ease of installation and use. Having extra files to deal with (especially for new Linux users), and having to make sure they are placed in the appropriate locations, can complicate things a little. I'm not saying the statement regarding this was in any way incorrect. But it was however, a choice I made purposefully in the interest of simplicity for new users.

The reason I bother with doing a root test is that some users may choose to manually start and stop the firewall from time to time. Although this wouldn't be the case for most folks, there are those who do (like me since I like tinkering with my firewall settings). This root test is a gentle "reminder" that the script needs to be run with root privs. that's all.

My test for legal startup arguments was indeed silly! I'll admit it! I took that part of the script from a firewall script that I wrote a few years ago when I was first learning how to write scripts. In any case, you'll now find that I've incorporated a nice little case statement as was suggested. Thanks for the tip!

Whether or not one logs dropped traffic is silly would be a matter of opinion I believe. I agree that for most applications, you don't want it. However, there have been times that my firewall logs have been tremendously useful when debugging new "features" that I've added to my firewall. That's the nice thing about the ability to turn it on and off! If one doesn't want the extra noise in their logfiles, by all means, turn it off!

Regarding the verbosity of the script... Yes! I agree that most of the time you won't have need for the script to be verbose. As was mentioned, an init script is usually fairly silent. So, I've provided an option to make the script run silently. For those who want to run it manually and get some feedback, they can make it verbose. Again, thanks for the tip!

My reasoning for adding the script's ability to set ip_foward, tcp_syncookies, and rp_filter came from a book I read called, "Linux Firewalls." I merely took it for face value and figured that the author of the book would know what he was talking about. Apparently I missed something there. However, since those things are already handled in the networking scripts, as was mentioned previously, I've decided to take heed of the advice given and remove them from the script.

Egress filtering... well, there are several schools of thought on that one. Unfortunately I didn't take the time to decide what side of the fence I was on when I wrote the script. So, in the hopes of keeping the script as user-friendly as possible, I've decided to eliminate egress filtering for the most part. I may add the ability of the script to maybe pull in a support file which contains a whole set of user defined rules regarding egress filtering but for now, I've decided to focus on ingress filtering and connection tracking relative to that. Now that my focus has been adjusted, I was able to clean up the ruleset substantially. This is probably one of the changes that had the biggest impact on the new script. As a side thought, I happen to prefer a firewall with egress filtering but the added extra complexity is sometimes questionable. I feel like this would be a case where that applies. Thanks for helping me focus on that!

The last thing I'll address is why I've made variables for port numbers. While true, if the port number for a given service will ALWAYS be a particular number it's best to hard code the port number in the script, this isn't the case with some peoples' servers. HTTP servers are commonly found on ports other than port 80. SSH servers are being run on non-standard ports to avoid the plentiful attacks of recent, from malicious scripts that only scan the well-know port associated with SSH. For whatever the reason, the script's ability to accomodate these non-standard configurations only adds versatility.

In closing, I'd like to offer my thanks for the tips (many of which I've incorporated) that everyone has provided thus far. I believe the script is much better now than it was but I know there are things that can be done to improve it so if you have any comments, I'm all ears! :D

---

### Post by dataw0lf on 2005-07-21
[QUOTE=asimon]This looks very much like security by obscurity, doesn't it?[/QUOTE]

More like security through misdirection.  

'Security through obscurity' is usually directed towards those who change their services fingerprints, default ports, etc (which often compromises the viability of said service).  THIS method does no such thing;  it just confuses and oft times will turn away any potential cracker because they're getting wacky returns from their port scanner.

---

### Post by skyboy on 2005-07-22
Hi, 
I have to say that this version is much clearer the previous one.
I have one question though : 
Is it possible to apply the firewall on any interface (eth0, ath0, ...) without having to change the EXTIF ? and I run to interface at the same time, and I like to apply firewall settings on "any" interface. Would it be possible to enable adding EXTIF = "any" ??
thanks

---

### Post by LordHunter317 on 2005-07-22
> **robert_pectol]My reasoning for not putting the script variables in /etc/defaults was simply for ease of installation and use.[/quote]Wonderful, but this makes it harder on users, not eaiser.  It's mostly nonstandard behavior, and having to edit an actual script scares them off.  Editing a file that appears to be just configuration settings is much eaiser to a new user.

> Having extra files to deal with (especially for new Linux users), and having to make sure they are placed in the appropriate locations, can complicate things a little.If they can't copy two files to the right location, it's reasonable to argue that they won't be able to run the script correctly, either.  Really.

> But it was however, a choice I made purposefully in the interest of simplicity for new users.Not to be excessively harsh, but it's the wrong one.  said:**
> My reasoning for adding the script's ability to set ip_foward, tcp_syncookies, and rp_filter came from a book I read called, "Linux Firewalls." I merely took it for face value and figured that the author of the book would know what he was talking about.In this case, the book isn't at fault, beyond the fact that it strives to be distro-indepenent (not an inherently bad thing), but certain network behaviors are handled by the distro automatically.  And overriding provided behavior in this manner isn't a good thing.

> Egress filtering... well, there are several schools of thought on that one. Generally, egress filtering on a single host makes little sense.  The most common exception is a server hosted in a co-lo facility, or any other network you don't control.  There, egress filtering can be worthwhile.  

Otherwise, it makes more sense to do it on network borders, since you have to do filtering there anyway.

You still didn't remove that mess of ICMP rules, they are not needed.  ICMP traffic in response to an existing connection (which all of that is) is automatically handled by  the RELATED state match.

You still have "--sport $UNPRIVPORTS" in several places.  It's wrong, drop it.  You're filtering out legtimate traffic with it.  There's no requirement that client traffic originate from ports >1024, and occasionally, it will originate from a low port.

---

### Post by robert_pectol on 2005-07-22
> Wonderful, but this makes it harder on users, not eaiser. It's mostly nonstandard behavior, and having to edit an actual script scares them off. Editing a file that appears to be just configuration settings is much eaiser to a new user.
I see! Well, if the general concensus is that it makes it more difficult, then I'll be glad to change it to conform to a more standard behavior. Consider it added to the list of "things to do."

> Not to be excessively harsh, but it's the wrong one.
Thanks for being so tactfully blunt! No really, I appreciate the comments!

> In this case, the book isn't at fault, beyond the fact that it strives to be distro-indepenent (not an inherently bad thing), but certain network behaviors are handled by the distro automatically. And overriding provided behavior in this manner isn't a good thing.
I guess part of the issue is that I'm a relative newcomer to Ubuntu and am still learning the particulars of this distro. That's the great thing about getting acquainted with new distros. You get to learn new things! Thanks for the clarification.

> Generally, egress filtering on a single host makes little sense. The most common exception is a server hosted in a co-lo facility, or any other network you don't control. There, egress filtering can be worthwhile.
Otherwise, it makes more sense to do it on network borders, since you have to do filtering there anyway.
If one has total control over the network to which he or she is connected, then great! They can take care of egress filtering on the network border and it is truly better that way. However, most users don't have that ability and most ISPs have very little egress filtering in place. The extent of the end user's network, over which they have control, ends at the cable/DSL modem. If for nothing else, egress filtering on their PC can keep them from becoming a spam relay or any number of other sources of evil traffic. Consider the case where a host has been compromised with a malicious virus or worm. Egress filtering may very well be the reason it doesn't spread to other hosts or propagate its payload effectively. For those reasons I don't completely discount the option to use egress filtering on an end-user's PC. Again, it comes down to firewall complexity versus level of protection. At what point does one decide that it's not worth the extra hassle? That point probably varies quite a bit from person to person. For the masses however, I'd say that egress filtering on their PCs probably isn't worth the added complexity hence my decision to remove it from the script (for now). But I disagree that, "Generally, egress filtering on a single host makes little sense."

> You still didn't remove that mess of ICMP rules, they are not needed. ICMP traffic in response to an existing connection (which all of that is) is automatically handled by the RELATED state match.
That was an oversight on my part. It'll be taken care of in the next revision.

> You still have "--sport $UNPRIVPORTS" in several places. It's wrong, drop it. You're filtering out legtimate traffic with it. There's no requirement that client traffic originate from ports >1024, and occasionally, it will originate from a low port.
Yeah... not very commonly though. This is again, some of the "spillover" from one of my old firewall scripts, from which this one was partially derived. I put those in there because the firewall book I was studying recommended it. I do question whether it's worthwhile under most circumstances however. Since I don't have a truly compelling reason to leave them in, I'll do as you suggested and remove them. I'd rather not chance it and block legit traffic. Thanks for pointing that out!

I'll post back again when I've made more changes to the script. Thanks again for your inputs.

---

### Post by robert_pectol on 2005-07-22
[QUOTE=skyboy]Hi, 
I have to say that this version is much clearer the previous one.
I have one question though : 
Is it possible to apply the firewall on any interface (eth0, ath0, ...) without having to change the EXTIF ? and I run to interface at the same time, and I like to apply firewall settings on "any" interface. Would it be possible to enable adding EXTIF = "any" ??
thanks[/QUOTE]

Thanks for the comments. I'm glad it's a bit easier to understand than the original. In answer to your first question, Yes, the script should ideally be able to accomodate any network interface although it probably could use some testing in that area. Interested? :)

In answer to your second question, Yes. The script could be modified to apply to all interfaces on the system but it would be by not specifying an interface at all instead of specifying each one. If it needs to be selective as to which interfaces it applies (some but not all), then it would have to include a ruleset for each interface. So, yes. It could be done either way. If that is something that would be desirable, then I'll consider adding that capability. If it doesn't end up being included in the official script, I can always help you put together a modified one that will do what you want.

---

### Post by LordHunter317 on 2005-07-22
[QUOTE=robert_pectol]If for nothing else, egress filtering on their PC can keep them from becoming a spam relay or any number of other sources of evil traffic.[/quote]The problem is, how do you tell based on IP and TCP/UDP headers, what traffic is good and bad, for your average client workstation?

The answer is: you can't.  Which is why egress filtering (at the level iptables provides, anyway) rarely makes sense on a single host.  To be more clear from above, it only makes sense when:[list][*]You can classify **all** outgoing traffic based solely on information in TCP/UDP and IP headers.  This restricts you to generally servers that have fixed roles operating on fixed ports,[*]and The network the machine exists on is beyond your control, so you can't filter at a higher level.[/list]

> For those reasons I don't completely discount the option to use egress filtering on an end-user's PC.Wonderful.  Write me a egress filtering solution that doesn't interfer with my ability to use *any* application I willfully install.  You'll quickly find you can't do that with iptables alone.  You might be able to do with layer-7 filtering, but you'll likely end up being either way too permissive or way too strict.  Neither of which is acceptable.

> But I disagree that, "Generally, egress filtering on a single host makes little sense."But it does, because you can't classify the traffic well enough to make it useful.

---

### Post by robert_pectol on 2005-07-22
Ok. I've further modified the firewall script to incorporate more of the numerous suggestions. At this point, I think it's a decent firewall for most any workstation or end-user's PC. Although not very feature full, it should provide a nice, safe, and stateful firewall for your Ubuntu box. Please give it a try and let me know what you think. It can be downloaded here:
 [http://rob.pectol.com/content/view/2/1/](http://rob.pectol.com/content/view/2/1/)
or viewed here:
 [http://rob.pectol.com/ubuntu-firewall.txt](http://rob.pectol.com/ubuntu-firewall.txt)
 
Please note that the script itself should now be located within your /etc/init.d/ directory. The separate init script that I made available for the original version is no longer needed. The script should be called directly. If that isn't the best way to do it, please, someone speak up and let me know. Also note that in the interest of keeping compliant with standard file locations, etc., I've included a separate firewall config file that is to be located within your /etc/default/ directory. The config file is commented well enough that configuration should still be very easy. The config file can be viewed here:
[http://rob.pectol.com/ubuntu-firewall-cfg](http://rob.pectol.com/ubuntu-firewall-cfg)

Let me know what you think!

Here are a couple of things I'm pondering regarding possible future additions to the script:


[list]
[*]Adding static rules to "back up" the stateful ones. Maybe this isn't worth it since the firewall is meant for a workstation or desktop machine. If it were being used on maybe a busy server or something similar, possibly only then would it be viable. What do you think?
[*]Adding the ability to apply the firewall to just one or all interfaces on the system. Or maybe even just some of the interfaces (although this is starting to deviate from the typical desktop machine). Any inputs?
[/list]Thanks everyone!

---

### Post by LordHunter317 on 2005-07-22
Can you post a version with a .txt extension so I can look it over?  Stupid firewall here blocks stuff based on mime type and is too restrictive.

> Adding static rules to "back up" the stateful ones.No, this will just lower the security the script provides.  One the points of stateful filtering is it makes eaiser to match packet content to where they logically belong in a connection (i.e., SYN only at start of connection).

---

### Post by robert_pectol on 2005-07-22
I've got a symlink to it with a .txt extension so it should be viewable at:
[http://rob.pectol.com/ubuntu-firewall.txt]("http://rob.pectol.com/ubuntu-firewall.txt")

On the static rules... Yeah, that was the conclusion I was coming to but wanted to hear others' inputs. Thanks again for looking the script over! Let me know what you think. Your suggestions have been excellent!

---

### Post by robert_pectol on 2005-08-04
I've had a chance to add some extra functionality to the firewall.  There's still a couple of things I'd still like to address but they are very minor and can wait until the next release.  This version is now more versatile and supports more configurations.  If the user requires specifed ports, either UDP or TCP, for a particular server application, it is now easily handled in the config file.  If you don't yet have a firewall for your Ubuntu Box, give this one a try!  It's bundled with a small README file and should be trivial to impliment on your box.  Thanks to all who have downloaded, used, and given feedback on it.  I invite all to do so by visiting the following link:

[http://rob.pectol.com/content/view/2/1/](http://rob.pectol.com/content/view/2/1/)

Rob

---

### Post by robert_pectol on 2005-08-05
It now supports multiple interfaces and Network Address Translation!  Let me know how it works for you!

[http://rob.pectol.com/content/view/2/1/](http://rob.pectol.com/content/view/2/1/)

---

### Post by reidi on 2005-10-27
The ongoing dialog between robert_pectol and LordHunter317 I think exemplifies the creative and synergistic possiblilities in the open-source movement.

Thank you "robert" for all your hard work, and for tuning your elegant contribution based on feedback.  Thanks to LordHunter317 for direct, constructive, and apparently (I can hardly spell firwall) expert input.

---

### Post by isaric on 2006-01-13
I use 
[http://rob.pectol.com/content/view/14/29/]("http://rob.pectol.com/content/view/14/29/")
For MySecureShell [http://mysecureshell.free.fr/]("http://mysecureshell.free.fr/")
And I want  use for FREEBOX TV (in french)
It should be known that the port 8080 TCP and 1234 UDP are used. 
The port 1234 UDP for stream to FREEBOX (routeur ADSL). 
Network port TCP 1234 goes towards address 212.27.38.253

The port 8080 TCP is used so that the freebox recovers the playlist and sends the instruction of reading, pauses, etc with VLC. The transfer are done by using address IP 212.27.38.253. It is necessary to open the port 8080 TCP towards the address of the station &#233;x&#233;cutant VLC.

In VLC I have :
```
 ...Sending request: SETUP rtsp://212.27.38.253/freeboxtv/201 RTSP/1.0
CSeq: 3
Transport: RTP/AVP;unicast;mode=play;destination=192.168.0.1;
client_port=**32782-32783**;server_port=**32768-32769**
```

I try help here 
[http://forum.ubuntu-fr.org/viewtopic.php?pid=167645#p167645]("http://forum.ubuntu-fr.org/viewtopic.php?pid=167645#p167645")

I did not find an answer. I am in France and I hope to be clear?

Photo VLC
r&#233;seau udp/rtp port 1234 [http://isaric.cof.free.fr/vlc1.png](http://isaric.cof.free.fr/vlc1.png)
flux output rtp port 1234 et port audio 1230 [http://isaric.cof.free.fr/vlc2.png](http://isaric.cof.free.fr/vlc2.png)
D&#233;multiplexeur RTP/RTSP/SDP (utilisant Live.com udp port b&#233;ta crazy 31337 [http://isaric.cof.free.fr/vlc3.png](http://isaric.cof.free.fr/vlc3.png)

---

### Post by isaric on 2006-01-15
I continue here
[http://forum.ubuntu-fr.org/viewtopic.php?pid=164808#p164808]("http://forum.ubuntu-fr.org/viewtopic.php?pid=164808#p164808")

---

### Post by elliot on 2006-02-09
Robert, this script is just what I've been trying to develop for quite some time. Thanks.
Just one question though, you have the option to log packets to syslog, would it be possible to log them to an iptables.log file?  I have experimented with this using:

iptables -A OUTPUT -j LOG --log-level 6

and then in /etc/syslog.conf putting a line to throw kern.6 into an iptables.log file, but it seems hackish.  I'm just looking for some way to really separate all the iptables logs from the rest of the system.
I'd love to hear everyone's thoughts.

---

### Post by robert_pectol on 2006-02-13
I see nothing wrong with the way you're doing it.  That's how I've done it in the past.  That being said, there *may* be better ways to do it.  Unfortunately I don't know what to suggest.  Perhaps some userspace logging scheme would do what you want.  Look at the --ulog flag options for more info but it looks like your logging mechanism would need to be able to collect multicast packets over a netlink socket.  Sounds a bit more involved than how you're doing it at the moment!  Anyone else have a suggestion?  Anyway, good luck with it.

---

### Post by jimwillsher on 2006-02-14
I know I'm probably leaving myself open to abuse here, so all I ask is that you're not rude!

My server is behind a NAT router, and I have certain ports forwarded (specifically, 25 and 80). Given that the Ubuntu kernel will drop malformed packets anyway, can anyone convince me to start setting up rules in iptables? It seems pointless, given that the kernel and the rotuer will ensure that only valid traffic comes my way. I don't even have port 22 open as I connect to my VPN (router) before using SSH.

It's a server-only, running apache and postfix.

Happy to set it up if it's recommended, but I just can't see what value it would give me - other than the admin overhead. If I do set it up, would the following be all I needed?

```
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -p tcp --dport smtp -j ACCEPT
sudo iptables -A INPUT -p tcp --dport http -j ACCEPT
sudo iptables -A INPUT -j DROP

```

Many thanks!


Jim

---

### Post by robert_pectol on 2006-02-15
If your NAT router is doing it's job, then only inbound traffic to your ports 25 and 80 will be routed to your PC.  The daemons which listen on those ports should only allow "sane" connections, while discarding the rest.  And yes, the kernel should discard malformed packets.  So you probably don't need to bother with host-based filtering of those services.  That being said, if the listening services bound to those ports don't give you enough control over who should be able to access them, then maybe you should consider some local filtering.  Examples include servers that don't give the option to listen on particular devices (loopback, eth0, etc.), servers that don't allow for ACLs, or if you wanted to limit connectivity from clients based on MAC address, etc.  When you start requiring finer granularity over the control of your services, then host-based filtering becomes more useful.  Another case where host-based filtering is valuable would be in a scenerio where your server box is on an "untrusted" network such as at a co-lo.  But that's another discussion.

There are those who would argue that the more "rings of security" you can add, the better off you are.  I used to be more of that mindset but now only in moderation.  Your particular circumstances and requirements will be your guide, obviously.  You see, there comes a point where the trade-off becomes no longer worth it, due to the extremely small gains in security vs. extra admin overhead.  You just have to decide where that point is for you (or your organization).  We have an Ubuntu server box that provides various services including file storage, as well as Internet connectivity to the rest of the computers at our location.  You better believe that box has a nice, tight firewall policy!  However, none of the computers behind it are firewalled and yet, some of them even offer publicly available services via port forwarding from the Ubuntu server.  For us, it's not worth the extra admin overhead involved with maintaining firewalls on each of the internal hosts.  However, you or your organization may deem it necessary, based on your requirements, policies, etc.

So that's the long (and opinionated) answer to your question.  :)

---

### Post by jimwillsher on 2006-02-15
Hi Robert,

Yes, your answer is very opinionated. But that's exactly what I wanted, the opinion of somebody who has been here before. And you have confirmed all my own thoughts.

The only public services I have available are ones which require no filtering, as they are web-available and therefore require to be available to everyone. Any other services are for my LAN only, and those ports aren't forwarded on the router, so they are safe too.

And "my organisation" is my own LAN, my Ubuntu box is a webserver in my attic, on my ADSL line. There's only it and a couple of Windows PCs on the LAN, both of which are using the Windows firewall.

So I think I'm pretty safe. Adding IPTables stuff would only add rules which are already covered by the router, so they would never find any packets to reject. Unnecessary overhead.

So I think I'll stick with an empty firewall list for now, and only start to use it if the need arises.

Thank you for your valuable and detailed thoughts.


Jim

---

### Post by John.Michael.Kane on 2006-02-26
Does anyone have this working on their desktop or laptop? 
Is this an inbound only blocking script?
What ports does it leave open, and what ports are closed?

Any people using this script on desktop or laptop please post how it has worked for you, and any problems you had with it.

---

### Post by nanotube on 2006-02-27
while robert's script is quite nice, as a home user with no services running, i find that i am quite happy with a simple ruleset that simply allows anything out, allows established,related in, and of course allows loopback. nice and simple. :) as a "regular" desktop user, there really is no need for anything so complex.

see my firewall setup in the link in my sig (choose firewall from the contents. :) )

---

### Post by Mustard on 2006-03-07
I'm interested in checking it out, but I've spent most of my time in this thread just following the conversation. :)

I have some questions though....

Currently I have no services running on my system, but would like to consider the option.  What type of situations for a desktop user would this script be most useful for?  What advantages does it have over the default settings for Ubuntu?

---

### Post by robert_pectol on 2006-03-08
For a desktop user, it only provides limited usefulness.  The truth is, most Linux desktop users only benefit marginally from running a local firewall but there are exceptions depending on the circumstances.  Again, if you want tighter control over who will have access to the services on your box, a local firewall may come in handy.  If you participate on, "untrusted" networks such as a school LAN or Internet Cafe, then one might benefit from a local firewall (also depending on the circumstances).  Generally speaking though, most home users are behind devices such as NAT routers which essentially create local, "trusted" networks for them.  A host-based firewall in this scenerio would probably be more of a liability than an asset.  Again, it's highly situation dependent but if one could generalize, I think that would be it.

The Ubuntu-firewall script, although perfectly useable on a desktop machine, was written more for the server arena.  It's stateful packet inspection and ability to turn your box into a NAT routing firewall are some of it's useful features.  Many folks are using in on their boxes to provide Internet Connection Sharing for their home or small office networks, etc.  Ubuntu-firewall in conjunction with Squid and Samba make for a feature-packed, file-serving, transparent proxy and NAT server!  It's all about options and if your NAT router is a linux box, you've got endless options!  Ubuntu-firewall can be extremely useful in a case such as this.

---

### Post by ethoslite on 2007-04-06
As I sit here reading through the helpful thread, I can't help but feel overwhelmed :)

I have heard others describe Security as a process, I agree.  It seems to take much effort to harden and protect what is so valuable to us.

Robert, it appears you have written a great script and firewall settings.  

I read about Firestarter and its ability to configure iptables to your tailoring.  Does Robert Pectol's Ubuntu-firewall script stand superb against something like Firestarter?

Thanks...

---

