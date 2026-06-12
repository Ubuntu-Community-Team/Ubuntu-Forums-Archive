---
title: "Secure Shell Tools for over the web"
date: 2013-04-17
forum: Server Platforms
---

### Post by AmbiguousOutlier on 2013-04-17
Hello, I've set up OpenSSH which works fine locally. However what tools would you recommend that work over the internet and can be easily installed at work behind a proxy server on a windows machine?

---

### Post by prodigy_ on 2013-04-17
SSH does work over the Internet (though you need port forwarding unless the server is directly connected to the Internet). [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) is a commonly used Windows client.

I never tried to SSH through proxy but it should be possible:
[http://www.techtalkz.com/blog/tips-n-tricks/how-to-use-ssh-putty-behind-a-proxy-firewall.html](http://www.techtalkz.com/blog/tips-n-tricks/how-to-use-ssh-putty-behind-a-proxy-firewall.html)

---

### Post by Lars Noodén on 2013-04-17
If you're stuck on a Windows client then PuTTY is the way to go.  There is also [portable PuTTY](http://portableapps.com/apps/internet/putty_portable), too.

What kind of proxy are you talking about?  Most set ups let SSH pass right through.  If you have a proxy that you must log into with SSH before connecting further, then you should look into Jump Hosts and that kind of thing.

---

### Post by AmbiguousOutlier on 2013-04-17
Cheers both, I popped home forwarded 22 to my server, came back to work and logged in via putty, and to my surprise it worked first time.

I'm now happily playing on my server whilst I should be working. :)

---

### Post by Lars Noodén on 2013-04-17
If you check your logs you can probably see that crackers are hammering away at your SSH server.  There are two useful things to do.  One is to disable root logins.  (PermitRootLogin No)  Root is already disabled in Ubuntu, but this is just crossing the ts and dotting the is.  The other is to disable password authentication (PasswordAuthentication no) and [use keys with a good passphrase](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) to connect.  That will prevent bruteforce attacks from guessing your password.  See the manual page for [sshd_config](http://manpages.ubuntu.com/manpages/quantal/en/man5/sshd_config.5.html) for more options and explanations.

---

### Post by AmbiguousOutlier on 2013-04-17
grep sshd.\*Failed /var/log/auth.log | less
grep sshd.\*Did /var/log/auth.log | less

produces;

Apr 17 12:54:19 Tomato sshd[24650]: Did not receive identification string from 83.244.225.145

Does that mean someone tried to get in? 

I couldn't get the keys to work over the LAN I kept getting "Agent admitted failure to sign using the key."

---

### Post by CharlesA on 2013-04-17
[This]("https://discussion.dreamhost.com/thread-127627.html") might be of help. I don't use any agent to remember my passphrase, so I enter it whenever I need to connect.

---

### Post by Lars Noodén on 2013-04-17
You'll get things like this, when people try to get in.  Largely it's automated and distributed:

```

Apr 16 00:28:14 lubuntu sshd[22515]: Failed password for invalid user admin from *xx.yy.zz.aa* port 34953 ssh2

```

To get keys working, you need a key pair and the public key needs to be copied over to the server and put in ~/.ssh/authorized_keys.  The whole key has to stay unbroken on one single line.  

Then to connect, you can reference the private key directly:

```

ssh -i ~/.ssh/server.key rhysgm@*xx.yy.zz.aa*

```

Or you can load it into the agent first, and let that worry about the key.  This is good if you're going to log in multiple times in short order.

```

ssh-add ~/.ssh/server.key
ssh rhysgm@*xx.yy.zz.aa*

```

Did you do those steps?

---

### Post by CharlesA on 2013-04-17
+1 to Lars. I use logwatch to keep an eye on my logs so I don't have to check them manually on the server every day.

I checked my VPS and this is what logwatch said:

```
--------------------- SSHD Begin ------------------------ 

 
 Didn't receive an ident from these IPs:
    200.77.161.1 (200-77-161-1.cable.dyn.cablevision.net.mx): 1 Time(s)
    202.121.166.203: 1 Time(s)
    202.28.123.194: 1 Time(s)
    54.251.250.122 (ec2-54-251-250-122.ap-southeast-1.compute.amazonaws.com): 1 Time(s)
    79.133.201.90: 1 Time(s)
 
 Illegal users from:
    86.109.100.24: 6 times
       teamspeak: 2 times
       nagios: 1 time
       oracle: 1 time
       postgres: 1 time
       test: 1 time
    96.45.18.226: 2 times
       nagios: 1 time
       teamspeak: 1 time
    115.238.73.16: 7 times
       oracle: 3 times
       msr: 1 time
       nagios: 1 time
       test: 1 time
       user0: 1 time
    183.62.232.93: 202 times
       oracle: 11 times
       user0: 6 times
       i-heart: 4 times
       diskbook: 3 times
       mircte: 3 times
       nagios: 3 times
       test: 3 times
       webmaster: 3 times
       www: 3 times
       bash: 2 times
       cwalsh: 2 times
       dolby: 2 times
       eddy: 2 times
       eduis: 2 times
       firefox: 2 times
       forevermd: 2 times
       guest: 2 times
       hub: 2 times
       mpsoc: 2 times
       mysqll: 2 times
       public: 2 times
       robertas: 2 times
       savitarna: 2 times
       ss2701: 2 times
       tadas: 2 times
       2012eduworld-2: 1 time
       Giani: 1 time
       PruncuTz: 1 time
       a: 1 time
       ale: 1 time
       alumno: 1 time
       apple_search: 1 time
       appltest: 1 time
       appluat: 1 time
       arthur: 1 time
       best: 1 time
       bkalle: 1 time
       bluecore: 1 time
       brightcorea: 1 time
       cjh: 1 time
       cladhaire: 1 time
       content: 1 time
       crond: 1 time
       danger: 1 time
       db2inst1: 1 time
       ddtddt: 1 time
       demuji: 1 time
       deng: 1 time
       dmd: 1 time
       dna1admin: 1 time
       dwsadm: 1 time
       eb: 1 time
       eclasi: 1 time
       eggbreaker2: 1 time
       evil: 1 time
       ewt: 1 time
       filecoupon: 1 time
       fm: 1 time
       fslbsmo: 1 time
       ftp: 1 time
       ftp2: 1 time
       ftp_wooripa: 1 time
       ftpd: 1 time
       ftpuser: 1 time
       gamme: 1 time
       gis: 1 time
       gwool: 1 time
       herosys: 1 time
       hhzls: 1 time
       httpd: 1 time
       ic: 1 time
       idclicksucai: 1 time
       img_data: 1 time
       info: 1 time
       inx: 1 time
       ip: 1 time
       jboss: 1 time
       jhshin: 1 time
       joyko: 1 time
       kai: 1 time
       kkamja: 1 time
       langliguo: 1 time
       lday: 1 time
       lex: 1 time
       lions: 1 time
       lipo: 1 time
       lovetravel-ftp: 1 time
       luis: 1 time
       mark: 1 time
       mbkim: 1 time
       megafile: 1 time
       mercy: 1 time
       michael: 1 time
       mmroot: 1 time
       moon: 1 time
       mooon: 1 time
       msr: 1 time
       multirode: 1 time
       multitrode: 1 time
       mviara: 1 time
       mysql0: 1 time
       mythtv: 1 time
       netcool: 1 time
       network: 1 time
       nexus: 1 time
       oratest: 1 time
       organize1: 1 time
       pabon: 1 time
       paul: 1 time
       paulb: 1 time
       paulos: 1 time
       perfectpond.org: 1 time
       pjtas: 1 time
       plechlo: 1 time
       postgres: 1 time
       prince: 1 time
       prueba: 1 time
       quegen: 1 time
       rayyau: 1 time
       rob: 1 time
       royalsoft: 1 time
       rppt: 1 time
       sandbox: 1 time
       scott: 1 time
       search: 1 time
       server: 1 time
       shobo: 1 time
       sir: 1 time
       smcgrath: 1 time
       sshserver: 1 time
       ssl: 1 time
       suniltex: 1 time
       svn: 1 time
       swsgest: 1 time
       tanglp: 1 time
       taz: 1 time
       tazelaar: 1 time
       template5: 1 time
       tmax: 1 time
       tomcat: 1 time
       tommy: 1 time
       trustconsult: 1 time
       tryit: 1 time
       tst: 1 time
       ttf: 1 time
       user: 1 time
       utnet: 1 time
       veronique: 1 time
       vivian: 1 time
       vizz: 1 time
       web: 1 time
       whg: 1 time
       x: 1 time
       xmap: 1 time
       xtreme: 1 time
       yangjun: 1 time
 
 ---------------------- SSHD End ------------------------- 
```

Gee, I wonder if someone is trying to do an attack against my server...

---

### Post by Lars Noodén on 2013-04-17
Cool.  Thanks for the logwatch output, CharlesA.  Are the probes coming close enough together that rate limiting with IP tables could trim it down a little?  The ones I see against sshd come in kind of slowly and they seem to be hoping that a small percentage of a very, very large pool will match.

---

### Post by AmbiguousOutlier on 2013-04-17
Yep, keys are all working now, however I can't restart the sshd service. So will do a full reboot when I get back. 

Cheers guys.

---

### Post by Lars Noodén on 2013-04-17
Great.  No need for a reboot, though.  It's enough just to restart sshd.  That can be done with upstart.

```

sudo restart ssh

```

If you want to check the syntax of your changes to sshd_config first, you can use the -t option with sshd.

```

sudo /usr/sbin/sshd -t

```

If everything is ok, there will be no output.  It will complain if there is an error in the syntax.

---

### Post by CharlesA on 2013-04-17
> **Lars Noodén said:**
> Cool.  Thanks for the logwatch output, CharlesA.  Are the probes coming close enough together that rate limiting with IP tables could trim it down a little?  The ones I see against sshd come in kind of slowly and they seem to be hoping that a small percentage of a very, very large pool will match.

I guess. I don't really have any data from what it was like before I enabled rate limiting because I have always had the 10 minute lockout from the start. As far as general rate limiting goes, that was added a while ago, but I don't really have an exact date.

The number of tries I see seems to vary from day to day. I'm currently using these rules to deal with bruteforce attacks (even if they can't get in due to keys).

10 minute lockout:
```
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -m recent --set --name SSH --rsource
-A INPUT -m recent --update --seconds 600 --hitcount 4 --rttl --name SSH --rsource -j REJECT --reject-with icmp-port-unreachable

```

General rate limiting:
```
-A INPUT -p tcp -m state --state NEW -m limit --limit 30/min --limit-burst 5 -j ACCEPT
```

I have both these rules and a few more in a script I apply via iptables-restore.

Hrm. I just looked at the raw logs and it looks like the rule I have isn't blocking the IP for 10 mins after 4 connection attempts. Guess I will have to put in a ticket with my VPS provider to see what's up.

```
Apr 16 08:03:45 serenity sshd[31733]: Invalid user db2inst1 from 183.62.232.93
Apr 16 08:03:49 serenity sshd[31738]: Invalid user prueba from 183.62.232.93
Apr 16 08:03:53 serenity sshd[31742]: Invalid user postgres from 183.62.232.93
Apr 16 08:04:01 serenity sshd[31750]: Invalid user mythtv from 183.62.232.93
Apr 16 08:04:08 serenity sshd[31759]: Invalid user kai from 183.62.232.93
Apr 16 08:04:10 serenity sshd[31761]: Invalid user mmroot from 183.62.232.93
Apr 16 08:04:20 serenity sshd[31771]: Invalid user x from 183.62.232.93
Apr 16 08:04:22 serenity sshd[31773]: Invalid user user from 183.62.232.93
Apr 16 08:04:36 serenity sshd[31787]: Invalid user rob from 183.62.232.93
Apr 16 08:04:46 serenity sshd[31797]: Invalid user organize1 from 183.62.232.93
Apr 16 08:04:48 serenity sshd[31799]: Invalid user tommy from 183.62.232.93
Apr 16 08:05:13 serenity sshd[31826]: Invalid user www from 183.62.232.93
Apr 16 08:05:21 serenity sshd[31834]: Invalid user nagios from 183.62.232.93
Apr 16 08:05:44 serenity sshd[31860]: Invalid user alumno from 183.62.232.93
Apr 16 08:06:12 serenity sshd[31889]: Invalid user guest from 183.62.232.93
Apr 16 08:06:15 serenity sshd[31893]: Invalid user shobo from 183.62.232.93
Apr 16 08:06:23 serenity sshd[31901]: Invalid user oratest from 183.62.232.93
Apr 16 08:06:29 serenity sshd[31907]: Invalid user mircte from 183.62.232.93
Apr 16 08:06:31 serenity sshd[31909]: Invalid user eduis from 183.62.232.93
Apr 16 08:06:33 serenity sshd[31911]: Invalid user lions from 183.62.232.93
Apr 16 08:06:35 serenity sshd[31913]: Invalid user ftp_wooripa from 183.62.232.93
Apr 16 08:06:37 serenity sshd[31915]: Invalid user forevermd from 183.62.232.93
Apr 16 08:06:39 serenity sshd[31917]: Invalid user webmaster from 183.62.232.93
Apr 16 08:06:43 serenity sshd[31921]: Invalid user ewt from 183.62.232.93
Apr 16 08:06:47 serenity sshd[31925]: Invalid user rppt from 183.62.232.93
Apr 16 08:06:49 serenity sshd[31927]: Invalid user www from 183.62.232.93
Apr 16 08:06:51 serenity sshd[31929]: Invalid user fm from 183.62.232.93
Apr 16 08:06:56 serenity sshd[31935]: Invalid user Giani from 183.62.232.93
Apr 16 08:07:12 serenity sshd[31952]: Invalid user eb from 183.62.232.93
Apr 16 08:07:18 serenity sshd[31958]: Invalid user i-heart from 183.62.232.93
Apr 16 08:07:26 serenity sshd[31966]: Invalid user veronique from 183.62.232.93
Apr 16 08:07:28 serenity sshd[31968]: Invalid user web from 183.62.232.93
Apr 16 08:07:34 serenity sshd[31974]: Invalid user multitrode from 183.62.232.93
Apr 16 08:07:36 serenity sshd[31976]: Invalid user public from 183.62.232.93
Apr 16 08:07:41 serenity sshd[31982]: Invalid user multirode from 183.62.232.93
Apr 16 08:07:43 serenity sshd[31984]: Invalid user filecoupon from 183.62.232.93
Apr 16 08:07:51 serenity sshd[31992]: Invalid user eclasi from 183.62.232.93
Apr 16 08:07:55 serenity sshd[31996]: Invalid user apple_search from 183.62.232.93
Apr 16 08:07:59 serenity sshd[32000]: Invalid user content from 183.62.232.93
Apr 16 08:08:03 serenity sshd[32004]: Invalid user httpd from 183.62.232.93
Apr 16 08:08:05 serenity sshd[32007]: Invalid user yangjun from 183.62.232.93
Apr 16 08:08:07 serenity sshd[32009]: Invalid user trustconsult from 183.62.232.93
Apr 16 08:08:09 serenity sshd[32011]: Invalid user mircte from 183.62.232.93
Apr 16 08:08:11 serenity sshd[32013]: Invalid user mircte from 183.62.232.93
Apr 16 08:08:15 serenity sshd[32017]: Invalid user eduis from 183.62.232.93
Apr 16 08:08:20 serenity sshd[32023]: Invalid user ssl from 183.62.232.93
Apr 16 08:08:30 serenity sshd[32033]: Invalid user oracle from 183.62.232.93
Apr 16 08:08:34 serenity sshd[32037]: Invalid user oracle from 183.62.232.93
Apr 16 08:08:36 serenity sshd[32039]: Invalid user oracle from 183.62.232.93
Apr 16 08:08:40 serenity sshd[32043]: Invalid user smcgrath from 183.62.232.93
Apr 16 08:08:42 serenity sshd[32045]: Invalid user scott from 183.62.232.93
Apr 16 08:08:50 serenity sshd[32053]: Invalid user deng from 183.62.232.93
Apr 16 08:08:54 serenity sshd[32057]: Invalid user webmaster from 183.62.232.93
Apr 16 08:08:58 serenity sshd[32061]: Invalid user webmaster from 183.62.232.93
Apr 16 08:09:02 serenity sshd[32065]: Invalid user oracle from 183.62.232.93
Apr 16 08:09:04 serenity sshd[32082]: Invalid user nagios from 183.62.232.93
Apr 16 08:09:06 serenity sshd[32085]: Invalid user i-heart from 183.62.232.93
Apr 16 08:09:09 serenity sshd[32089]: Invalid user utnet from 183.62.232.93
Apr 16 08:09:15 serenity sshd[32095]: Invalid user mpsoc from 183.62.232.93
Apr 16 08:09:17 serenity sshd[32097]: Invalid user lipo from 183.62.232.93
Apr 16 08:09:25 serenity sshd[32105]: Invalid user brightcorea from 183.62.232.93
Apr 16 08:09:27 serenity sshd[32107]: Invalid user suniltex from 183.62.232.93
Apr 16 08:09:29 serenity sshd[32109]: Invalid user gwool from 183.62.232.93
Apr 16 08:09:31 serenity sshd[32111]: Invalid user kkamja from 183.62.232.93
Apr 16 08:09:33 serenity sshd[32113]: Invalid user forevermd from 183.62.232.93
Apr 16 08:09:35 serenity sshd[32115]: Invalid user quegen from 183.62.232.93
Apr 16 08:09:45 serenity sshd[32125]: Invalid user www from 183.62.232.93
Apr 16 08:09:52 serenity sshd[32133]: Invalid user ic from 183.62.232.93
Apr 16 08:09:58 serenity sshd[32139]: Invalid user sir from 183.62.232.93
Apr 16 08:10:12 serenity sshd[32152]: Invalid user ss2701 from 183.62.232.93
Apr 16 08:10:16 serenity sshd[32156]: Invalid user dwsadm from 183.62.232.93
Apr 16 08:10:26 serenity sshd[32166]: Invalid user mbkim from 183.62.232.93
Apr 16 08:10:30 serenity sshd[32170]: Invalid user jhshin from 183.62.232.93
Apr 16 08:10:32 serenity sshd[32172]: Invalid user nexus from 183.62.232.93
Apr 16 08:10:38 serenity sshd[32180]: Invalid user crond from 183.62.232.93
Apr 16 08:10:47 serenity sshd[32190]: Invalid user search from 183.62.232.93
Apr 16 08:10:49 serenity sshd[32192]: Invalid user ss2701 from 183.62.232.93
Apr 16 08:10:51 serenity sshd[32194]: Invalid user tst from 183.62.232.93
Apr 16 08:13:17 serenity sshd[32343]: Invalid user tryit from 183.62.232.93
Apr 16 08:13:23 serenity sshd[32350]: Invalid user luis from 183.62.232.93
Apr 16 08:13:25 serenity sshd[32352]: Invalid user ip from 183.62.232.93
Apr 16 08:13:27 serenity sshd[32354]: Invalid user mpsoc from 183.62.232.93
Apr 16 08:13:31 serenity sshd[32358]: Invalid user netcool from 183.62.232.93
Apr 16 08:14:20 serenity sshd[32409]: Invalid user public from 183.62.232.93
Apr 16 08:14:25 serenity sshd[32415]: Invalid user eggbreaker2 from 183.62.232.93
Apr 16 08:14:27 serenity sshd[32417]: Invalid user network from 183.62.232.93
Apr 16 08:14:56 serenity sshd[32443]: Invalid user xtreme from 183.62.232.93
Apr 16 08:15:00 serenity sshd[32447]: Invalid user ftpd from 183.62.232.93
Apr 16 08:15:02 serenity sshd[32449]: Invalid user ale from 183.62.232.93
Apr 16 08:15:09 serenity sshd[32458]: Invalid user hub from 183.62.232.93
Apr 16 08:15:21 serenity sshd[32470]: Invalid user inx from 183.62.232.93
Apr 16 08:15:29 serenity sshd[32480]: Invalid user oracle from 183.62.232.93
Apr 16 08:15:49 serenity sshd[32500]: Invalid user guest from 183.62.232.93
Apr 16 08:15:52 serenity sshd[32504]: Invalid user oracle from 183.62.232.93
Apr 16 08:16:12 serenity sshd[32525]: Invalid user msr from 183.62.232.93
Apr 16 08:16:16 serenity sshd[32529]: Invalid user ddtddt from 183.62.232.93
Apr 16 08:16:20 serenity sshd[32533]: Invalid user pjtas from 183.62.232.93
Apr 16 08:16:22 serenity sshd[32535]: Invalid user whg from 183.62.232.93
Apr 16 08:16:24 serenity sshd[32537]: Invalid user sandbox from 183.62.232.93
Apr 16 08:16:33 serenity sshd[32547]: Invalid user hub from 183.62.232.93
Apr 16 08:16:35 serenity sshd[32549]: Invalid user mooon from 183.62.232.93
Apr 16 08:16:37 serenity sshd[32551]: Invalid user bluecore from 183.62.232.93
Apr 16 08:16:39 serenity sshd[32553]: Invalid user cjh from 183.62.232.93
Apr 16 08:16:48 serenity sshd[32559]: Invalid user info from 183.62.232.93
Apr 16 08:16:50 serenity sshd[32561]: Invalid user demuji from 183.62.232.93
Apr 16 08:16:56 serenity sshd[32567]: Invalid user diskbook from 183.62.232.93
Apr 16 08:16:58 serenity sshd[32569]: Invalid user diskbook from 183.62.232.93
Apr 16 08:17:00 serenity sshd[32571]: Invalid user diskbook from 183.62.232.93
Apr 16 08:17:04 serenity sshd[32575]: Invalid user firefox from 183.62.232.93
Apr 16 08:17:06 serenity sshd[32578]: Invalid user user0 from 183.62.232.93
Apr 16 08:17:10 serenity sshd[32582]: Invalid user mysql0 from 183.62.232.93
Apr 16 08:17:12 serenity sshd[32584]: Invalid user user0 from 183.62.232.93
Apr 16 08:17:18 serenity sshd[32590]: Invalid user firefox from 183.62.232.93
Apr 16 08:17:21 serenity sshd[32594]: Invalid user user0 from 183.62.232.93
Apr 16 08:17:25 serenity sshd[32598]: Invalid user swsgest from 183.62.232.93
Apr 16 08:17:27 serenity sshd[32600]: Invalid user megafile from 183.62.232.93
Apr 16 08:17:29 serenity sshd[32602]: Invalid user i-heart from 183.62.232.93
Apr 16 08:17:31 serenity sshd[32604]: Invalid user i-heart from 183.62.232.93
Apr 16 08:17:35 serenity sshd[32608]: Invalid user bash from 183.62.232.93
Apr 16 08:17:39 serenity sshd[32612]: Invalid user taz from 183.62.232.93
Apr 16 08:17:43 serenity sshd[32616]: Invalid user PruncuTz from 183.62.232.93
Apr 16 08:17:49 serenity sshd[32622]: Invalid user paulb from 183.62.232.93
Apr 16 08:17:51 serenity sshd[32624]: Invalid user michael from 183.62.232.93
Apr 16 08:17:57 serenity sshd[32630]: Invalid user lday from 183.62.232.93
Apr 16 08:17:59 serenity sshd[32632]: Invalid user nagios from 183.62.232.93
Apr 16 08:18:04 serenity sshd[32639]: Invalid user svn from 183.62.232.93
Apr 16 08:18:14 serenity sshd[32649]: Invalid user joyko from 183.62.232.93
Apr 16 08:18:16 serenity sshd[32651]: Invalid user user0 from 183.62.232.93
Apr 16 08:18:22 serenity sshd[32657]: Invalid user sshserver from 183.62.232.93
Apr 16 08:18:28 serenity sshd[32663]: Invalid user server from 183.62.232.93
Apr 16 08:18:34 serenity sshd[32669]: Invalid user vivian from 183.62.232.93
Apr 16 08:18:36 serenity sshd[32671]: Invalid user prince from 183.62.232.93
Apr 16 08:18:40 serenity sshd[32675]: Invalid user tomcat from 183.62.232.93
Apr 16 08:18:46 serenity sshd[32681]: Invalid user lovetravel-ftp from 183.62.232.93
Apr 16 08:18:58 serenity sshd[32693]: Invalid user ftpuser from 183.62.232.93
Apr 16 08:19:06 serenity sshd[32702]: Invalid user idclicksucai from 183.62.232.93
Apr 16 08:19:07 serenity sshd[32704]: Invalid user gamme from 183.62.232.93
Apr 16 08:19:13 serenity sshd[32710]: Invalid user xmap from 183.62.232.93
Apr 16 08:19:24 serenity sshd[32718]: Invalid user mysqll from 183.62.232.93
Apr 16 08:19:26 serenity sshd[32720]: Invalid user test from 183.62.232.93
Apr 16 08:19:34 serenity sshd[32728]: Invalid user mysqll from 183.62.232.93
Apr 16 08:19:40 serenity sshd[32734]: Invalid user eddy from 183.62.232.93
Apr 16 08:19:48 serenity sshd[32742]: Invalid user eddy from 183.62.232.93
Apr 16 08:19:51 serenity sshd[32746]: Invalid user moon from 183.62.232.93
Apr 16 08:19:57 serenity sshd[32752]: Invalid user vizz from 183.62.232.93
Apr 16 08:19:59 serenity sshd[32754]: Invalid user herosys from 183.62.232.93
Apr 16 08:20:17 serenity sshd[305]: Invalid user img_data from 183.62.232.93
Apr 16 08:20:23 serenity sshd[311]: Invalid user hhzls from 183.62.232.93
Apr 16 08:20:27 serenity sshd[315]: Invalid user tanglp from 183.62.232.93
Apr 16 08:20:36 serenity sshd[327]: Invalid user ttf from 183.62.232.93
Apr 16 08:20:46 serenity sshd[337]: Invalid user template5 from 183.62.232.93
Apr 16 08:20:52 serenity sshd[343]: Invalid user appluat from 183.62.232.93
Apr 16 08:20:56 serenity sshd[347]: Invalid user appltest from 183.62.232.93
Apr 16 08:21:10 serenity sshd[362]: Invalid user plechlo from 183.62.232.93
Apr 16 08:21:12 serenity sshd[364]: Invalid user dmd from 183.62.232.93
Apr 16 08:21:14 serenity sshd[366]: Invalid user mviara from 183.62.232.93
Apr 16 08:21:50 serenity sshd[400]: Invalid user arthur from 183.62.232.93
Apr 16 08:21:52 serenity sshd[402]: Invalid user rayyau from 183.62.232.93
Apr 16 08:21:58 serenity sshd[408]: Invalid user user0 from 183.62.232.93
Apr 16 08:22:01 serenity sshd[413]: Invalid user user0 from 183.62.232.93
Apr 16 08:22:05 serenity sshd[419]: Invalid user mark from 183.62.232.93
Apr 16 08:22:37 serenity sshd[454]: Invalid user dolby from 183.62.232.93
Apr 16 08:22:39 serenity sshd[456]: Invalid user dolby from 183.62.232.93
Apr 16 08:22:41 serenity sshd[458]: Invalid user cladhaire from 183.62.232.93
Apr 16 08:22:42 serenity sshd[460]: Invalid user mercy from 183.62.232.93
Apr 16 08:22:46 serenity sshd[464]: Invalid user paulos from 183.62.232.93
Apr 16 08:22:48 serenity sshd[466]: Invalid user lex from 183.62.232.93
Apr 16 08:22:50 serenity sshd[468]: Invalid user bkalle from 183.62.232.93
Apr 16 08:22:52 serenity sshd[470]: Invalid user tazelaar from 183.62.232.93
Apr 16 08:22:54 serenity sshd[472]: Invalid user pabon from 183.62.232.93
Apr 16 08:23:02 serenity sshd[480]: Invalid user paul from 183.62.232.93
Apr 16 08:23:10 serenity sshd[489]: Invalid user cwalsh from 183.62.232.93
Apr 16 08:23:14 serenity sshd[493]: Invalid user cwalsh from 183.62.232.93
Apr 16 08:23:16 serenity sshd[495]: Invalid user evil from 183.62.232.93
Apr 16 08:23:48 serenity sshd[525]: Invalid user best from 183.62.232.93
Apr 16 08:24:27 serenity sshd[566]: Invalid user a from 183.62.232.93
Apr 16 08:24:29 serenity sshd[568]: Invalid user fslbsmo from 183.62.232.93
Apr 16 08:24:31 serenity sshd[570]: Invalid user danger from 183.62.232.93
Apr 16 08:24:33 serenity sshd[572]: Invalid user oracle from 183.62.232.93
Apr 16 08:24:35 serenity sshd[574]: Invalid user bash from 183.62.232.93
Apr 16 08:24:37 serenity sshd[576]: Invalid user oracle from 183.62.232.93
Apr 16 08:24:39 serenity sshd[578]: Invalid user oracle from 183.62.232.93
Apr 16 08:24:45 serenity sshd[584]: Invalid user dna1admin from 183.62.232.93
Apr 16 08:24:47 serenity sshd[586]: Invalid user test from 183.62.232.93
Apr 16 08:24:53 serenity sshd[592]: Invalid user oracle from 183.62.232.93
Apr 16 08:24:55 serenity sshd[594]: Invalid user tmax from 183.62.232.93
Apr 16 08:24:58 serenity sshd[598]: Invalid user langliguo from 183.62.232.93
Apr 16 08:25:00 serenity sshd[600]: Invalid user oracle from 183.62.232.93
Apr 16 08:25:08 serenity sshd[609]: Invalid user test from 183.62.232.93
Apr 16 08:25:18 serenity sshd[619]: Invalid user royalsoft from 183.62.232.93
Apr 16 08:25:22 serenity sshd[623]: Invalid user 2012eduworld-2 from 183.62.232.93
Apr 16 08:25:30 serenity sshd[633]: Invalid user perfectpond.org from 183.62.232.93
Apr 16 08:25:34 serenity sshd[637]: Invalid user gis from 183.62.232.93
Apr 16 08:25:43 serenity sshd[652]: Invalid user jboss from 183.62.232.93
Apr 16 08:25:47 serenity sshd[656]: Invalid user ftp from 183.62.232.93
Apr 16 08:26:04 serenity sshd[671]: Invalid user ftp2 from 183.62.232.93
Apr 16 08:26:06 serenity sshd[674]: Invalid user savitarna from 183.62.232.93
Apr 16 08:26:08 serenity sshd[676]: Invalid user robertas from 183.62.232.93
Apr 16 08:26:10 serenity sshd[678]: Invalid user tadas from 183.62.232.93
Apr 16 08:26:12 serenity sshd[680]: Invalid user tadas from 183.62.232.93
Apr 16 08:26:14 serenity sshd[682]: Invalid user robertas from 183.62.232.93
Apr 16 08:26:24 serenity sshd[692]: Invalid user savitarna from 183.62.232.93

```

EDIT: I guess I made a mistake with the rules for the SSH lockout. I found a nice set here: [https://we.riseup.net/debian/iptables-recent-module-and-hit-limits](https://we.riseup.net/debian/iptables-recent-module-and-hit-limits)

I don't see any difference between that one and the one I was using outside of the one I was using worked on my main home server, but not my test Debian box and not the VPS..

The rules in the above link are:

```
iptables -N SSHSCAN

iptables -A INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -j SSHSCAN 

iptables -A SSHSCAN -m recent --set --name SSH --rsource 
iptables -A SSHSCAN -m recent --update --seconds 3600 --hitcount 5 --name SSH --rsource -j LOG --log-prefix "Anti SSH-Bruteforce: " --log-level 6 
iptables -A SSHSCAN -m recent --update --seconds 3600 --hitcount 5 --name SSH --rsource -j DROP
```

---

### Post by lilledavy on 2013-04-20
Perhaps the tool "fail2ban" could be useful? It is automating the process of identifying failed login attempts and blocking the IP for an hour via iptables if more than 5 failed attempts are detected within an hour (all parameters configurable, I usually use 10 hrs block, 3 attempts within an hour). It works by watching the system log(s) and there are filters for SSH, VSFTP, HTTP and more.
It's available in the standard repos, I installed simply with "sudo apt-get install fail2ban" and afterwards edited the configuration files in /etc/fail2ban/. (Set the interesting parameters and enable the tests in /etc/fail2ban/jail.local.)

---

### Post by Lars Noodén on 2013-04-20
CharlesA, thanks for the updated iptables rules.

---

### Post by CharlesA on 2013-04-20
Lars, Doug S helped me with streamlining a couple of my rules and you can find his suggestions in this thread:
[http://ubuntuforums.org/showthread.php?t=2137073](http://ubuntuforums.org/showthread.php?t=2137073)

Pretty neat.

---

### Post by kevdog on 2013-04-21
If you are only running the ssh server for yourself, I'd definitely recommend the AllowUser <username> option within the config file -- this would only the user with the specific name in.  This is just one more step to hardening your ssh server.  In addition using a rate limit or hit count that could be used within iptables.  You could also change to a different port -- but as you said you are working behind a proxy and the proxy might not let out different ports.  I use a port knocker on one of my machines to dynamically alter the firewall from outside the firewall, however in most cases this is probably superfluous.

---

