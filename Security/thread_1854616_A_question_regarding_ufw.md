---
title: "A question regarding ufw"
date: 2011-10-04
forum: Security
---

### Post by jsvidyad on 2011-10-04
Hello,
  I run ubuntu 10.04.3 LTS.

  When I enabled ufw, there was a message saying that ufw would be enabled at system startup. Does this mean that ufw will be enabled automatically when ubuntu starts? Is any user intervention necessary once ubuntu starts to get ufw to start and set the iptables rules? I am asking this because on older versions of ubuntu, I was using firestarter and it was supposed to set the iptables rules automatically when ubuntu starts. So, I always assumed that the firewall rules would be set without any user intervention during boot-up.But, on one occasion, after booting up, I found that there were no iptables rules set(they were empty and all default rules were set to ACCEPT) and I had to start firestarter manually to set the iptables rules. Has anyone had a problem like this with ufw? Right now, once I log in, I use the command "sudo ufw status verbose" to make sure that ufw is active. Is this step necessary? Or once ufw is set, can I just forget about checking to see if the firewall is active at later boot ups?

---

### Post by Dangertux on 2011-10-04
UFW will start automatically at boot time. You don't need to do anything, also be aware it is a front end for iptables like firestarter. 

Also the ufw default policy is drop input accept forward and output

---

### Post by jsvidyad on 2011-10-04
So, I don't need to test the status of ufw using the "sudo ufw status verbose" command? Is there any chance of ufw showing the issue I had with firestarter as I mentioned in the earlier post?

---

### Post by Dangertux on 2011-10-04
I've not seen ufw just not set policies according to the rules you set out. If you're that concerned I would just write an iptables script and set it to run when your networking starts. That's just me though, I don't really use  UFW or other front ends so I don't have a whole lot of experience with them just magically deciding not to work.

Is there a particular reason you need a firewall? IE : Are you trying to block some  service from being accessible from the internet? In a default configuration Ubuntu is not running any services so there really isn't anything to firewall.

---

### Post by jsvidyad on 2011-10-04
> **Dangertux said:**
> I've not seen ufw just not set policies according to the rules you set out. If you're that concerned I would just write an iptables script and set it to run when your networking starts. That's just me though, I don't really use  UFW or other front ends so I don't have a whole lot of experience with them just magically deciding not to work.

Is there a particular reason you need a firewall? IE : Are you trying to block some  service from being accessible from the internet? In a default configuration Ubuntu is not running any services so there really isn't anything to firewall.

I am not running any service. Ubuntu is installed on a desktop workstation. I am using the firewall as an additional layer of security, just in case I inadvertently install some server while installing other packages.

  I was concerned because of the earlier issue I had with firestarter. Despite the fact that I was told that firestarter would set the iptables automatically when ubuntu starts, it didn't do that once. Can you tell me how ufw loads the iptables rules automatically at boot up time? Then, maybe I can check to see if all the necessary files are in the correct place.

---

### Post by Dangertux on 2011-10-04
> **jsvidyad said:**
> I am not running any service. Ubuntu is installed on a desktop workstation. I am using the firewall as an additional layer of security, just in case I inadvertently install some server while installing other packages.

  I was concerned because of the earlier issue I had with firestarter. Despite the fact that I was told that firestarter would set the iptables automatically when ubuntu starts, it didn't do that once. Can you tell me how ufw loads the iptables rules automatically at boot up time? Then, maybe I can check to see if all the necessary files are in the correct place.

UFW user rules are stored in /lib/ufw/user.rules and user6.rules (for ipv6).

UFW default rules are stored in /etc/ufw/before.rules /etc/ufw/after.rules and /etc/ufw/before6.rules and after6.rules (for ipv6).

---

### Post by jsvidyad on 2011-10-04
> **Dangertux said:**
> UFW user rules are stored in /lib/ufw/user.rules and user6.rules (for ipv6).

UFW default rules are stored in /etc/ufw/before.rules /etc/ufw/after.rules and /etc/ufw/before6.rules and after6.rules (for ipv6).

Can you tell me where the scripts which are loaded at boot-time are and how they are used? Then, maybe I can check those scripts to make sure that ufw does set the iptables rules when ubuntu starts. I just wanted to say that everytime I checked the status of ufw after logging in, I always found it active. I never ever found it inactive the way I found with firestarter.

---

### Post by Dangertux on 2011-10-04
I gave you the locations the rules are stored, so I'm not sure what else you want in regard of scripts, but the easiest way to see if your firewall rules are there is.

```

sudo iptables -L

```That being said, if you're not setting any rules, IE: you're just doing

```

sudo ufw enable

```the only thing that would be added in terms of iptables would be

```

iptables -P INPUT DROP

```So there really isn't anything to see unless you add a rule.

---

### Post by jsvidyad on 2011-10-05
I was hoping you could tell me how the ufw rules are loaded at system startup.

---

### Post by jsvidyad on 2011-10-05
Maybe I wasn't clear. ufw just sets the iptables rules, right?? I just wanted to know where the script that sets iptables rules at startup is and how it sets the iptables rules

---

### Post by Dangertux on 2011-10-05
> **jsvidyad said:**
> Maybe I wasn't clear. ufw just sets the iptables rules, right?? I just wanted to know where the script that sets iptables rules at startup is and how it sets the iptables rules

You are correct, ufw is just a front end for iptables. I told you earlier in the post where the scripts that ufw loads at start up are located. To reiterate that point

UFW default rules (the policies and rules that come with UFW by default) are stored in

```

/etc/ufw/before.rules
/etc/ufw/after.rules
/etc/ufw/before6.rules
/etc/ufw/after6.rules

```UFW user rules (rules created by you, example : allowing traffic to SSH) are stored in

```

/lib/ufw/user.rules
/lib/ufw/user6.rules

```These files are loaded by UFW when it starts, if it is scheduled as an upstart job (starts at boot time) they will be loaded then. Otherwise they will be loaded when you give the

```

sudo ufw enable

```command.

As far as iptables goes, you can create a script anywhere to interact with that, starting an iptables script is often done either via an upstart job, using the service iptables-save command , or adding the iptables script to the network interface's pre-up.d startup scripts.

Outside of that I'm not sure what else you're looking for.

---

### Post by jsvidyad on 2011-10-06
How do I find if the ufw is set up as an upstart job?

Do you think I am un-necessarily worrying and that ufw will set the necessary iptables rules automatically during system startup? I have been concerned with this because of my earlier surprise with firestarter. 

It would be nice if ufw is a set and forget firewall, the kind which is set up on the windows 7 computers I have to use in my office.

---

### Post by jsvidyad on 2011-10-06
Can you please help me with this?

---

### Post by Dangertux on 2011-10-06
> **jsvidyad said:**
> How do I find if the ufw is set up as an upstart job?

Do you think I am un-necessarily worrying and that ufw will set the necessary iptables rules automatically during system startup? I have been concerned with this because of my earlier surprise with firestarter. 

It would be nice if ufw is a set and forget firewall, the kind which is set up on the windows 7 computers I have to use in my office.

Hey , if you run the followign command

```

intictl show-config

```it will list all the current upstart jobs if ufw is an upstart job it will show something like this

```

ufw
start on ((starting network-interface or starting network-manager) or starting networking)
stop on runlevel [!023456]

```As for your other questions, yes I do think you're being a little too worried, particularly considering firewalls really don't do much in a default configuration if you don't have any services running. As far as being worried about installing a server accidentally goes, I really don't think that's likely. You don't just go looking for tetris and come back with apache. So I think that may be a little too paranoid of a stance.

Like I said, in its default configuration, with a default Ubuntu install UFW really won't do much for you. The bottom line is UFW is set and forget, Firestarter has problems, it's been out of development for a long time, and really was never that great of a front end to begin with.

---

### Post by jsvidyad on 2011-10-07
So, what you are saying is that once ufw has been enabled and configured, it will automatically set the firewall(iptables) rules at startup everytime the system is turned on and boots into ubuntu? Does this mean that I don't have to check to see if ufw is active and if the iptables rules have been set each time I boot into ubuntu? The only reason I was worried about this was because as I mentioned earlier, firestarter promised the same but did not deliver the results once when I checked the iptables rules(they were empty with default rule set to ACCEPT).

---

### Post by Dangertux on 2011-10-07
> **jsvidyad said:**
> So, what you are saying is that once ufw has been enabled and configured, it will automatically set the firewall(iptables) rules at startup everytime the system is turned on and boots into ubuntu? Does this mean that I don't have to check to see if ufw is active and if the iptables rules have been set each time I boot into ubuntu? The only reason I was worried about this was because as I mentioned earlier, firestarter promised the same but did not deliver the results once when I checked the iptables rules(they were empty with default rule set to ACCEPT).

Yes -- ufw will set the rules at start up.

You really need to understand though, and I'm not sure you're clear on this part. UFW's default policy IE: if you type

```

sudo ufw enable

```

is this to DENY INPUT, ALLOW FORWARD and ALLOW OUTPUT. This is not the most restrictive policy in the world, however if you are just worried about accidentally installing a service and you don't have any currently installed it's fine.

As I said earlier Firestarter was very buggy. As you said earlier, you're currently not running any services so really a default UFW firewall will do nothing that your system isn't already doing.

I'm sorry if I sound short, I'm not trying to I'm just trying to make sure you understand what I'm saying.

---

### Post by jsvidyad on 2011-10-08
The default rules right now seem to be INPUT-DROP,FORWARD-DROP and OUTPUT-ACCEPT. I just want to make sure someone else can't get into the computer. For that, these rules are good enough, right?

---

### Post by The Cog on 2011-10-08
Assuming that ufw is configured as an upstart job, you will find its configuration file in /etc/init, probably /etc/init/ufw.conf. upstart is a program loaded very early in the boot process, and uses the rules in this folder to decide when other processes should be started and stopped.

---

### Post by Dangertux on 2011-10-08
> **jsvidyad said:**
> The default rules right now seem to be INPUT-DROP,FORWARD-DROP and OUTPUT-ACCEPT. I just want to make sure someone else can't get into the computer. For that, these rules are good enough, right?

That's a very broad question : and a firewall is not a one stop shop for that. 

To elaborate a lot of people misunderstand what a firewall is. A firewall is essentially a filter for incoming and outgoing connections, nothing more nothing less. It can become more complicated when you're adding a deep packet inspection firewall and or intrusion prevention system which Ubuntu does not come with by default. You would have to install something along the lines of Snort or OSSEC to have that functionality.

In all reality a firewall protecting nothing with unrestrictive outbound rules is essentially useless. If you would like to understand more about how attackers can "get into your computer" remotely , and how a firewall can and can not help you I would suggest reading [this ]("http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/"). I wrote it to address this particular question that a lot of people have.

In lieu of that I suggest that if you are truly paranoid about system security, you look into other things besides a firewall. NoScript and similar browser addons, mandatory access controls such as Apparmor (comes with Ubuntu but needs to be configured) or SELinux, and ensuring that you're giving your programs proper permissions in the discretionary access control scheme.

These are all things that can help you secure your system, additionally don't download from untrusted repositories, and generally use common sense.

But ultimately no a firewall is not the end all be all of system security.

---

### Post by jsvidyad on 2012-12-14
Hello,

  I want to get something clarified. When I have set up ufw on a laptop and I switch between wired and wireless connections, what happens? Will the firewall be up and running in both cases? Or when I switch, will I have to restart ufw? Does the same firewall rules protect me for both wired and wireless connections? Do the firewall rules set up by ufw depend on the kind of network interface used for the network connection in any way?

---

### Post by Hungry Man on 2012-12-14
Switching connections shouldn't change anything.

---

### Post by JKyleOKC on 2012-12-14
> **jsvidyad said:**
> Do the firewall rules set up by ufw depend on the kind of network interface used for the network connection in any way?They can, but don't have to. It depends entirely on how each specific rule is written.

That is, a rule can be specified as applying to just one specific network interface, and if that's done the rule will be ignored for all other interfaces. However in the absence of such a specification, it will apply to all of them.

You would have to examine the rules that UFW generated for your system to determine which is the case; UFW lets you do it either way.

---

### Post by Ms. Daisy on 2012-12-14
So unless you specify a particular network interface, then the default for ufw, gufw, and iptables is to apply to all interfaces, correct?

---

### Post by haqking on 2012-12-14
> **Ms. Daisy said:**
> So unless you specify a particular network interface, then the default for ufw, gufw, and iptables is to apply to all interfaces, correct?

from the man page:

> By default, ufw will apply rules to all available interfaces. To limit  this,  specify DIRECTION on INTERFACE, where DIRECTION is one of in or out (interface aliases  are  not  supported).   For example,  to  allow  all  new incoming http connections on eth0, use: ufw allow in on eth0 to any port 80 proto tcp

---

### Post by JKyleOKC on 2012-12-14
And for iptables itself, it's the "-i" and "-o" options in each rule. Most of the time an interface is specified, but not always. If not, the rule applies to all of them.

---

### Post by jsvidyad on 2013-01-18
Hello, 

   I usually set up ufw with the default rules of incoming:deny and outgoing:allow. Now, I know that these ufw default firewall settings (when ufw is enabled) protect my computer when I'm connected to the internet via a wired connection since I have used these default ufw settings on desktops running ubuntu which have wired connections to the internet and ufw is set up and enabled on those desktops. Is the working of the above default ufw settings dependent on the network interface used for internet access?  I plan to install ubuntu on a laptop and use the laptop's wireless interface to connect to wireless networks. Will the above mentioned default ufw settings for the ufw firewall work for the wireless interface of my laptop too? Will the ufw firewall with the above mentioned default ufw settings work to protect my laptop while my laptop is connected via a wireless connection to the internet  using my laptop's wireless interface?

---

### Post by haqking on 2013-01-18
> **jsvidyad said:**
> Hello, 

   I usually set up ufw with the default rules of incoming:deny and outgoing:allow. Now, I know that these ufw default firewall settings (when ufw is enabled) protect my computer when I'm connected to the internet via a wired connection since I have used these default ufw settings on desktops running ubuntu which have wired connections to the internet and ufw is set up and enabled on those desktops. Is the working of the above default ufw settings dependent on the network interface used for internet access?  I plan to install ubuntu on a laptop and use the laptop's wireless interface to connect to wireless networks. Will the above mentioned default ufw settings for the ufw firewall work for the wireless interface of my laptop too? Will the ufw firewall with the above mentioned default ufw settings work to protect my laptop while my laptop is connected via a wireless connection to the internet  using my laptop's wireless interface?

2 posts above, [post #24]("http://ubuntuforums.org/showpost.php?p=12405208&postcount=24")

---

### Post by jsvidyad on 2013-01-19
When I set the default incoming rule to deny and the default outgoing rule to allow, I don't specify any network interface. So, those settings should work for any network interface(more specifically the ethernet wired interface and the wireless interface) and the ufw firewall will protect my computer irrespective of which network interface I am using to connect to the internet, right? 

   I was using firestarter till like 2 years ago and in firestarter, when I configure firestarter, I had to specify which network interface was connected to the internet and the rules were set only for that interface. If I later started using another network interface to connect to the internet, I had to re-configure firestarter and specify the new network interface as the internet connected network device. If I didn't do that, the firestarter firewall would become inactive and wouldn't protect my computer. Now, when setting up and configuring the ufw firewall, I didn't have to specify any network interface as the internet connected network device. So, I wasn't sure if my settings  for ufw were were valid and whether ufw was active and protecting my computer when I use any one of the different network interfaces available to connect to the internet, irrespective of which network interface I was using to connect to the internet. More specifically, I wasn't sure if my ufw firewall was active and protecting my computer no matter whether I was using the ethernet wired interface or the wireless interface as the internet connected device in order to connect to the internet. Also, I wasn't sure(I still am not) if I had to re-configure the ufw firewall when I switched from using one network interface to another network interface in order to connect to the internet.

---

### Post by haqking on 2013-01-19
> **jsvidyad said:**
> When I set the default incoming rule to deny and the default outgoing rule to allow, I don't specify any network interface. So, those settings should work for any network interface(more specifically the ethernet wired interface and the wireless interface) and the ufw firewall will protect my computer irrespective of which network interface I am using to connect to the internet, right? 

   I was using firestarter till like 2 years ago and in firestarter, when I configure firestarter, I had to specify which network interface was connected to the internet and the rules were set only for that interface. If I later started using another network interface to connect to the internet, I had to re-configure firestarter and specify the new network interface as the internet connected network device. If I didn't do that, the firestarter firewall would become inactive and wouldn't protect my computer. Now, when setting up and configuring the ufw firewall, I didn't have to specify any network interface as the internet connected network device. So, I wasn't sure if my settings  for ufw were were valid and whether ufw was active and protecting my computer when I use any one of the different network interfaces available to connect to the internet, irrespective of which network interface I was using to connect to the internet. More specifically, I wasn't sure if my ufw firewall was active and protecting my computer no matter whether I was using the ethernet wired interface or the wireless interface as the internet connected device in order to connect to the internet. Also, I wasn't sure(I still am not) if I had to re-configure the ufw firewall when I switched from using one network interface to another network interface in order to connect to the internet.

From post #24

> By default, ufw will apply rules to all available interfaces.Firestarter is out of date and buggy.

```
sudo ufw status
```will tell you if its active

---

### Post by jsvidyad on 2013-01-25
When I set the ufw default rules as incoming:deny and outgoing:allow(i.e. deny incoming connections and allow outgoing connections), I do not specify any network interface. So, those default rules should apply to all interfaces, right? When the above default rules are set for the ufw firewall and the ufw firewall has been enabled on my computer, the ufw firewall will be active and protecting my computer irrespective of which network interface I'm using to connect to the internet, right? More specifically, after setting the above default rules and enabling the ufw firewall on my laptop, the ufw firewall will apply those default rules and protect my laptop irrespective of whether I use the wired ethernet interface on my laptop or the wireless interface of my laptop to connect my laptop to the internet, right?

---

### Post by Ms. Daisy on 2013-01-25
How many times do you want an answer?

> By default, ufw will apply rules to all available interfaces.

---

### Post by jsvidyad on 2013-01-27
> **Ms. Daisy said:**
> How many times do you want an answer?

Hello,

    What I understood is that the statement "By default, ufw will apply rules to all available interfaces" is applicable only for user added rules. What I mean by user added rules are rules such as the one where the user tells the ufw/Gufw firewall to accept all inbound network traffic from a certain ip address or the one where the user tells the ufw/Gufw firewall to accept all network traffic inbound on a certain port number. 

  What I am asking is about the default incoming and outgoing rules we set up when we enable/activate ufw initially and then do the initial configuration of ufw. I have set up these default rules as incoming:deny and outgoing:allow(i.e. deny all incoming connections and allow all outgoing connections). Are these default incoming and outgoing rules for ufw also independent of which network interface is used to make the connection to the internet? More specifically, what I am asking is that once I set up the above mentioned default incoming and outgoing rules for ufw, will the ufw firewall enforce these rules and protect my laptop from the internet traffic irrespective of whether I'm using my laptop's wired ethernet network interface or my laptop's wireless network interface to connect to the internet.

---

### Post by haqking on 2013-01-27
> **jsvidyad said:**
> Hello,

    What I understood is that the statement "By default, ufw will apply rules to all available interfaces" is applicable only for user added rules. What I mean by user added rules are rules such as the one where the user tells the ufw/Gufw firewall to accept all inbound network traffic from a certain ip address or the one where the user tells the ufw/Gufw firewall to accept all network traffic inbound on a certain port number. 

  What I am asking is about the default incoming and outgoing rules we set up when we enable/activate Gufw initially and then do the initial configuration of Gufw. I have set up these default rules as incoming:deny and outgoing:allow(i.e. deny all incoming connections and allow all outgoing connections). Are these default incoming and outgoing rules for Gufw also independent of which network interface is used to make the connection to the internet? More specifically, what I am asking is that once I set up the above mentioned default incoming and outgoing rules for Gufw, will the Gufw firewall enforce these rules and protect my laptop from the internet traffic irrespective of whether I'm using my laptop's wired ethernet network interface or my laptop's wireless network interface to connect to the internet.

unless you specify otherwise, rules apply to all available interfaces.


```
man ufw
```

---

### Post by jsvidyad on 2013-01-27
> **haqking said:**
> unless you specify otherwise, rules apply to all available interfaces.


```
man ufw
```

So, what you are saying is that the default incoming and outgoing rules I set for the ufw firewall(incoming:deny and outgoing:allow) will be applied and effective and will protect my computer irrespective of through which network interface the computer is connected to the internet?

---

### Post by conquerorodueko on 2013-01-28
jsvidyad - YES - exactly as you said it!!!

In ufw you can configure rules to a selected/specific interfaces. e.g. - 
eth - [Direct cable connection to a router] differentiated by number 0,1,2... to as many as you have
wlan - [Wireless connection to a router] differentiated by number 0,1,2... to as many as you have

SO AS LONG AS YOU HAVE NOT MANUALLY SPECIFIED IT THEN IT APPLIES TO ALL REGARDLESS {inclusive and irrespective any/all of eth{0,1,2...} wlan{0,1,2...}

CLEAR?

---

### Post by jsvidyad on 2013-01-29
Yes, it's clear. A couple more questions.

1) What you said applies to both ufw and Gufw, right? For both ufw and Gufw, the default incoming and outgoing rules I set of incoming:deny and outgoing:allow will apply and be effective for all the network interfaces of my computer and will protect my computer irrespective of through which network interface my computer is connected to the internet, right?  And for both ufw and Gufw, any firewall rules I set, which does not explicitly specify any specific network interface, will apply to all network interfaces and will be applied and be in effect irrespective of through which network interface my computer is connected to the internet, right?

2) You said that the default incoming and outgoing rules and the user added rules, which do not explicitly specify any specific network interface, will be effective and applied irrespective of through which network interface my computer is connected to the internet, right? Does this imply that if I switch between using my laptop's wired ethernet interface or my laptop's wireless interface to connect to the internet, I do not have to re-configure or change any of the settings in ufw? I can just switch to using a different network interface for internet access without changing any of the firewall settings?

---

### Post by haqking on 2013-01-29
> **jsvidyad said:**
> Yes, it's clear. A couple more questions.

1) What you said applies to both ufw and Gufw, right? For both ufw and Gufw, the default incoming and outgoing rules I set of incoming:deny and outgoing:allow will apply and be effective for all the network interfaces of my computer and will protect my computer irrespective of through which network interface my computer is connected to the internet, right?  And for both ufw and Gufw, any firewall rules I set, which does not explicitly specify any specific network interface, will apply to all network interfaces and will be applied and be in effect irrespective of through which network interface my computer is connected to the internet, right?

2) You said that the default incoming and outgoing rules and the user added rules, which do not explicitly specify any specific network interface, will be effective and applied irrespective of through which network interface my computer is connected to the internet, right? Does this imply that if I switch between using my laptop's wired ethernet interface or my laptop's wireless interface to connect to the internet, I do not have to re-configure or change any of the settings in ufw? I can just switch to using a different network interface for internet access without changing any of the firewall settings?

are you trolling ?

GUFW is just a GUI for UFW which is merely an interface to IPTables which is the built in firewall in the Linux kernel, UFW/GUFW is not a firewall on its own.

and the rules will apply to all interfaces by default unless you ask them not to !!!!!!!!!!!! I dont know how to say this again in another way

---

### Post by jsvidyad on 2013-01-29
No, I'm not trolling. I just want to be sure of some things.

  Since you say that Gufw is just a GUI for ufw, the statement that ufw rules will apply to all network interfaces unless that rule is specified as applying only to one particular network interface, will apply to Gufw rules too, right?

  Also, if the Gufw/ufw rules apply to all network interfaces unless that rule is specified as applying only to one particular network interface, doesn't that imply that when my computer switches from using one network interface to using another network interface for accessing the internet, I don't have to re-configure the Gufw/ufw firewall or change its settings or rules in any way in order to account for the change of internet connected network interface(Of course, assuming I haven't set any rules which apply only for a specific network interface)?

Please answer the above two questions.

---

### Post by haqking on 2013-01-29
> **jsvidyad said:**
> No, I'm not trolling. I just want to be sure of some things.

  Since you say that Gufw is just a GUI for ufw, the statement that ufw rules will apply to all network interfaces unless that rule is specified as applying only to one particular network interface, will apply to Gufw rules too, right?

  Also, if the Gufw/ufw rules apply to all network interfaces unless that rule is specified as applying only to one particular network interface, doesn't that imply that when my computer switches from using one network interface to using another network interface for accessing the internet, I don't have to re-configure the Gufw/ufw firewall or change its settings or rules in any way in order to account for the change of internet connected network interface(Of course, assuming I haven't set any rules which apply only for a specific network interface)?

Please answer the above two questions.

Rules will apply to ALL interfaces unless you specify otherwise.

Please read it, digest it and then read it again, I cant think of another way to say the same thing again.

---

### Post by jsvidyad on 2013-01-29
> **haqking said:**
> Rules will apply to ALL interfaces unless you specify otherwise.

Hello, I got what you are saying. But the above statement can lead to some inferences. My two questions are stating two of the inferences that can be drawn from the above statement and I'm just asking you to confirm that those inferences are correct. So, can you please read those two questions and reply specifically to them?

---

### Post by steeldriver on 2013-01-29
why don't you open up your /var/log/ufw.log and have a look?

:popcorn:

---

### Post by bodhi.zazen on 2013-01-29
> **jsvidyad said:**
> Hello, I got what you are saying. But the above statement can lead to some inferences. My two questions are stating two of the inferences that can be drawn from the above statement and I'm just asking you to confirm that those inferences are correct. So, can you please read those two questions and reply specifically to them?

I have read through this thread and I agree your questions have been asked and answered. The gufw / ufw / iptables rules apply to all interfaces all the time unless you specify an interface. Only you know what rules you applied.

---

### Post by conquerorodueko on 2013-02-27
JSVIDYAD... 
There is the [before.rules] which comes pre-set unless manually changed
There is the [before6.rules] which comes pre-set unless manually changed
There is the [after.rules] which comes pre-set unless manually changed
Then there is the [user.rules] which come pre-set to block nothing and which is what GUFW alters in in user-space environment

The combination of all these [before.rules],[before6.rules],[after.rules] and [user.rules] is the UFW. 

GUFW is just a user space environment to change the [user.rules] just so you do not have to use the [command prompt]... To manually edit the other rules, you will have to do so using the [command prompt], unless some genius helps create a user space environment to easily do it, hence not needing to do so through the [command prompt].... clear?

---

### Post by jsvidyad on 2013-03-08
Hello,

  First of all, I would like to reiterate that I'm not trolling. I'm just a bit obsessive when it comes to security. I always like to get small points cleared up. So, please bear with me and please do not get upset.

    From the posts in this thread I understood that since I don't specify any network interface when I specify the ufw default rules(Incoming:Deny and Outgoing:Allow), they will be in effect and those firewall rules will protect my computer irrespective of which network interface I use to connect to the internet(essentially these rules are effective irrespective of whether I use my laptop's ethernet interface or my laptop's wireless network interface to connect to the internet).

So, based on the above statement, I can make the following inference:
When I switch between using the ethernet interface or the wireless network interface of my laptop to connect to the internet, I do not have to reconfigure the ufw firewall for the new interface in any way since the default rules given above are valid for both the interfaces(I am not setting any rules other than the default rules mentioned above). So, I can switch from using one network interface to another to connect to the internet without making any changes to the ufw firewall but still the default rules mentioned above will be enforced and will protect my laptop. Is this inference correct?

Also, since as mentioned in an earlier post Gufw is just a GUI for ufw, all the statements in this thread about the dependence/independence of firewall rules on the network interface and inferences from those statements should apply to Gufw too, right?

---

### Post by haqking on 2013-03-08
> **jsvidyad said:**
> hello,

  first of all, i would like to reiterate that i'm not trolling. I'm just a bit obsessive when it comes to security. I always like to get small points cleared up. So, please bear with me and please do not get upset.

    From the posts in this thread i understood that since i don't specify any network interface when i specify the ufw default rules(incoming:deny and outgoing:allow), they will be in effect and those firewall rules will protect my computer irrespective of which network interface i use to connect to the internet(essentially these rules are effective irrespective of whether i use my laptop's ethernet interface or my laptop's wireless network interface to connect to the internet).

So, based on the above statement, i can make the following inference:
When i switch between using the ethernet interface or the wireless network interface of my laptop to connect to the internet, i do not have to reconfigure the ufw firewall for the new interface in any way since the default rules given above are valid for both the interfaces(i am not setting any rules other than the default rules mentioned above). So, i can switch from using one network interface to another to connect to the internet without making any changes to the ufw firewall but still the default rules mentioned above will be enforced and will protect my laptop. Is this inference correct?

Also, since as mentioned in an earlier post gufw is just a gui for ufw, all the statements in this thread about the dependence/independence of firewall rules on the network interface and inferences from those statements should apply to gufw too, right?

yes

---

### Post by jsvidyad on 2013-03-16
Is the "yes" the answer to both the questions I asked?

---

### Post by mörgæs on 2013-03-16
Here comes another yes - and with this I believe the thread has run its course.
Closing.

---

