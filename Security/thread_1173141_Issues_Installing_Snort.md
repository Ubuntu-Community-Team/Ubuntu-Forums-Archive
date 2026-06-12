---
title: "Issues Installing Snort"
date: 2009-05-29
forum: Security
---

### Post by pheonixace_7 on 2009-05-29
Hello everybody. I recently installed Ubuntu after years of windows admin work (please don't shoot me) and am absolutely loving it. I am now setting up snort in Ubuntu Jaunty and am having some issues that I was hoping you might could point me in the right direction on. I have been following a guide located [here]("https://help.ubuntu.com/community/SnortIDS") but ran into a couple of snags. I installed MySQL, created the permissions, and installed Snort (after some trial and error), but when it mentions to do:
```
sudo /etc/init.d/snort status
tail /var/log/daemon.log
```
to verify that snort started I get an error message:
> May 29 11:21:23 is-d0068nix snort[3454]: Warning: flowbits key 'community_uri.size.1050' is set but not ever checked. 
May 29 11:21:23 is-d0068nix snort[3454]: Warning: flowbits key 'smb.tree.create.llsrpc' is set but not ever checked. 
May 29 11:21:23 is-d0068nix snort[3454]: 37 out of 512 flowbits in use. 
May 29 11:21:23 is-d0068nix snort[3454]: Initializing daemon mode 
May 29 11:21:24 is-d0068nix snort[3455]: PID path stat checked out ok, PID path set to /var/run/ 
May 29 11:21:24 is-d0068nix snort[3455]: Writing PID "3455" to file "/var/run//snort_eth0.pid" 
May 29 11:21:24 is-d0068nix snort[3455]: Daemon initialized, signaled parent pid: 3454 
May 29 11:21:24 is-d0068nix snort[3454]: Daemon parent exiting 
May 29 11:21:24 is-d0068nix snort[3455]: database: must enter database name in configuration file  
May 29 11:21:24 is-d0068nix snort[3455]: FATAL ERROR:

I did some searches on that and found some people having the same issue, but I didn't really find any solutions to the issue. 

I'm not sure if this was a good idea or not, but I went on and continued the steps to see how far it would let me get. I made it down through the 
```
sudo apt-get -y install acidbase
```
step just fine and even went through the
```
sudo sed -i "s#allow\ from\ 127.0.0.0/255.0.0.0#allow\ from\ 127.0.0.0/255.0.0.0\ 10.10.1.10/255.255.255.0#" /etc/acidbase/apache.conf
```
step, but I'm not sure how to test to see if it works. I restarted apache and it said it restarted (I got the [OK] message), but when I try to open up the ACID page it won't load. I have a suspicion that once I get the first part in order the ACID part will either fall into place or I will have some better leads on how to troubleshoot it. I just included it in my post as steps that I have taken. 

I thank you in advance for any helpful pointers you may have. I hope everyone has a great weekend.

---

### Post by bodhi.zazen on 2009-05-29
I believe the problem is most likely with your sed line.

You need to change the "10.10.1.10/255.255.255.0" to your net mask , on a LAN most likely something like 192.168.0.0.

Of course the first time you ran the sed it changed the 127.0.0.0 to 10.01.1.10 so ...

you first need to determine your net mask Run```
/sbin/ifconfig
```

you will see a line similar to :

> inet addr:192.168.0.10  Bcast:192.168.1.255  Mask:255.255.255.0

so, in this example, you need 192.168.0.1/255.255.255.0

Open the file "/etc/acidbase/apache.conf" for editing and put in the correct information.

---

### Post by pheonixace_7 on 2009-06-01
I knew I forgot to mention something when I was writing that up. You're right, when I first started through the guide I did mess that up, but I caught it when I was going back through it to try and sort it out. I have the right IP/subnet info in there now. But when I run the /etc/init.d/snort status command I am getting "Failed" and if I run the tail /var/log/daemon.log I still get the same error messages.

---

### Post by bodhi.zazen on 2009-06-01
To be honest, the way that how-to uses sed it is confusing (the author uses sed to make changes to configuration files without explaining the changes, IMO).

This error :

> May 29 11:21:24 is-d0068nix snort[3455]: database: must enter database name in configuration file

means you need to use the correct mysql data base name in your snort config file.

---

### Post by pheonixace_7 on 2009-06-02
You know, that makes a lot of sense. Thanks for the tip. I'm not going to have time to try and fix it today, but hopefully I can work on it tomorrow. You've been a huge help. I'll update here when I am able to test this.

---

### Post by pheonixace_7 on 2009-06-05
I hate being "that guy" with all of the annoying questions, but this is really stumping me. I see what you're saying about needing the database name in the snort config (/etc/snort/snort.conf I assume), but I can't figure out where it is lacking the DB name. I went through and did a search for "database:" and "dbname" and all of those entries have the right name there. I also searched for "user=snort" to see if the database field all together was left out somehow and they seem to all be there (as best I can tell at least). 

Is there somewhere else I need to be entering that database name? Also, do you know of any good snort guides for Jaunty that may describe things a little better? I'm all for reading up on it and trying to figure it out, but I'm at a bit of a loss as to where to go. Thanks a bunch for all your help.

---

### Post by bodhi.zazen on 2009-06-05
I published a guide here :

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

And yes, the snort config file is verbose.

Personally I find it is easier to install snort from source , but it you use the repositories you might want to consider removing and re-installing it.

```
apt-get remove --purge snort
```

Also, if you installed from the repositories, you may need** **snort-mysql (not sure).

You also need some rules, so you may need** **snort-rules-default . oinkmaster can also be nice.

See a listing of the snort packages here :

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=snort&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=snort&searchon=name&subword=1&version=all&release=all)

I am not certain about snort in the repos as I find it is very easy to build from source ;)

---

### Post by pheonixace_7 on 2009-06-10
Thank you bodhi.zazen for all your help. After some more tinkering around I actually just scrapped the whole thing and am starting from scratch through your guide. It is already proving to be significantly easier because I know what things are doing. You have been both a huge help in this thread and in your guide. I'm still not completely finished with the install yet, but it is moving alongly very smoothly.

---

