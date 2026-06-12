---
title: "NTP master network time becomes unsynced!"
date: 2010-06-19
forum: Server Platforms
---

### Post by ThomWilhelm on 2010-06-19
Ok I have a really simple NTP setup for my local network, I only have one PC connected to the internet which receives NTP time, and then the other 2 computer use NTP to sync with this master server.

However, over the last week every few hours/days the "master" server's time becomes in the past, so it suddenly becomes 5-15 minutes behind the real time. The other 2 computers on the network don't usually sync to this PC as its time is probably considered incorrect.

All servers have Ubuntu 9.04 installed.

So the problem is something to do with the master time server receiving the correct time, here is its NTP.conf file:

[B]# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift

# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server ntp.ubuntu.com iburst
server pool.ntp.org iburst
server 127.127.1.0
fudge 127.127.1.0 stratum 10

# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
restrict 169.254.1.1 mask 255.255.0.0 nomodify notrap

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 169.254.255.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient[/B]

Any ideas as to why its time could suddenly jump backwards?

Thanks :popcorn:

---

### Post by denarced on 2010-06-20
The basics: it's actually connected to the internet?
I suppose you could try and add 5 more ntp servers to the list where it attempts to get the time. It's possible that those particular servers are down. Now that's something you could try but the part about 5-15 minutes offset in time is truly weird..

---

### Post by ThomWilhelm on 2010-06-20
Yes this computer is connected to the internet, its the only one on the network that is.

If I add lots of NTP servers in my ntp.conf, does it have any sort of intelligent detection system about which one to use? Or does it just use the first one in the list.

Next time this happens I will run ntpdate manually and see what I get...

---

### Post by ThomWilhelm on 2010-07-03
Hmmm this is still happening, I just rebooted and within 1 hour the master servers time was 30 seconds slow. But the other servers still have the correct time (not resyncing to this incorrect time)

So I tried resyncing manually:

root@webserver1:~# sudo ntpdate ntp.ubuntu.com
 3 Jul 12:50:08 ntpdate[2208]: the NTP socket is in use, exiting
root@webserver1:~# service ntp stop
 * Stopping NTP server ntpd                                              [ OK ] 
root@webserver1:~# sudo ntpdate ntp.ubuntu.com
 3 Jul 12:50:57 ntpdate[2246]: step time server 91.189.94.4 offset 32.804687 sec
root@webserver1:~# service ntp start
 * Starting NTP server ntpd                                              [ OK ] 

Weird because I have this server in my ntp.conf file I posted above! Any ideas anyone? ;)

---

### Post by ThomWilhelm on 2010-07-05
Have installed a shell script I call from PHP when this is detected:

service ntp stop; ntpdate ntp.ubuntu.com; service ntp start

Hope this helps until I resolve this.

---

### Post by tgalati4 on 2010-07-05
Could be a bad hardware clock.  Sync once, stop ntpd then measure time drift after 12 or 24 hours.  If greater than +/- 4 seconds/day, then your hardware clock is wonky.

If you enable the drift calculations you can get 0.1 millisecond accuracy by using 2nd-order thermal/diurnal drift correctors.  Of course, you need a working system clock.

dmesg | more

Look for clock errors.  Also check interrupts:

cat /proc/interrupts

A few other things to check:

What is your drift file?

tgalati4@tubuntu2:/var/lib/ntp$ cat ntp.drift 
-34.498

Enable statistics in the config file--remove the #.

I don't remember exactly what's in the file, but the "peers" file looks something like:

tgalati4@tubuntu2:/var/log/ntpstats$ cat peers
55384 749.805 204.13.164.164 9414 0.000127914 0.074257695 0.014842234 0.001554300
55384 816.850 64.73.32.135 9314 0.003633987 0.117148370 0.014828058 0.000697911
55384 972.798 17.151.16.20 9414 0.001035000 0.061050000 0.014823503 0.000153500
55384 978.793 131.216.22.24 9314 0.002291060 0.055374046 0.030407193 0.004113857
55384 986.801 72.254.0.254 9614 0.002358975 0.062982698 0.014839781 0.002272140
55384 1774.834 204.13.164.164 9414 0.000387290 0.074556371 0.014841819 0.000259376
55384 1839.879 64.73.32.135 9314 0.004550451 0.117813371 0.014818567 0.000916464
55384 1998.825 17.151.16.20 9414 0.000876500 0.059587000 0.014839842 0.000158500
55384 2003.821 131.216.22.24 9314 0.002649454 0.055702616 0.030404211 0.000358394
55384 2010.834 72.254.0.254 9614 0.005701455 0.068205057 0.014833192 0.003342480
55384 2799.861 204.13.164.164 9414 0.001297842 0.073503885 0.014841633 0.000910552
55384 2865.907 64.73.32.135 9314 0.004278532 0.117578801 0.014836203 0.000271920
55384 3024.855 17.151.16.20 9414 0.001053000 0.060772000 0.014847991 0.000176500
55384 3029.848 131.216.22.24 9314 -0.000097414 0.053951093 0.030410119 0.002746868
55384 3035.858 72.254.0.254 9614 0.002926758 0.062871089 0.014837269 0.002774696
55384 3823.890 204.13.164.164 9414 0.001651907 0.073952885 0.014834072 0.000354064
55384 3890.936 64.73.32.135 9314 0.004376441 0.118387324 0.014837498 0.000097910
55384 4048.882 17.151.16.20 9414 0.001116500 0.060037000 0.014837148 0.000063500
55384 4053.878 131.216.22.24 9314 0.000578186 0.055438092 0.030398171 0.000675600
55384 4059.899 72.254.0.254 9614 0.005574512 0.075723743 0.014831904 0.002647753
55384 4849.918 204.13.164.164 9414 0.002116580 0.073757562 0.014845144 0.000464674
55384 4914.964 64.73.32.135 9314 0.003137540 0.117703371 0.014830640 0.001238901
55384 5071.911 17.151.16.20 9314 0.001057500 0.060379000 0.014824317 0.000059000
55384 5079.906 131.216.22.24 9314 -0.000039604 0.054835093 0.030407076 0.000617790
55384 5082.915 72.254.0.254 9614 0.003291034 0.062965581 0.014821714 0.002283477
55384 5872.948 204.13.164.164 9414 0.002335411 0.074465180 0.014828332 0.000218831
55384 5941.149 64.73.32.135 9314 -0.072712117 0.274253847 0.014843297 0.075849657
55384 6094.940 17.151.16.20 9414 0.000795000 0.060708000 0.014817993 0.000262500
55384 6103.935 131.216.22.24 9314 -0.000406542 0.055819046 0.030396653 0.000366938
55384 6108.943 72.254.0.254 9614 0.002945849 0.063005312 0.014839031 0.000345185

It shows how your ntp clock varies from the ntp servers you are pinging.

---

### Post by ThomWilhelm on 2010-07-11
Ok I have disabled the NTP service for the afternoon will post up results of how far my computer has drifted later on.

I read that using as many NTP servers as possible is recommended so the computer can agree with the "majority" time. So when I restart config file will change to:

# You do need to talk to an NTP server or two (or three).
server ntp.ubuntu.com iburst
server pool.ntp.org iburst
server pool.ntp.org iburst
server ntp.ubuntu.com iburst
server 0.pool.ntp.org iburst
server 1.pool.ntp.org iburst
server 2.pool.ntp.org iburst
server 3.pool.ntp.org iburst
server time.nist.gov iburst
server time-a.nist.gov iburst
server time-b.nist.gov iburst
server time-a.timefreq.bldrdoc.gov iburst
server time-b.timefreq.bldrdoc.gov iburst
server time-c.timefreq.bldrdoc.gov iburst
server 127.127.1.0
fudge 127.127.1.0 stratum 10

Will see if this makes a difference. Thanks for your help so far.

---

### Post by ThomWilhelm on 2010-07-11
Ok had disabled NTP on the server I use on the network for master time for today and the time had not drifted even 1 second. I have started the NTP service with many more time servers. Will post back results next week.

---

### Post by ThomWilhelm on 2010-07-14
Doh! Even with all these servers listed in my ntp.conf I am still having the same problem. Doesn't seem like the hardware clock as I had disabled NTP with no major drift...

root@webserver1:~# service ntp stop; ntpdate ntp.ubuntu.com; service ntp start
 * Stopping NTP server ntpd                                              [ OK ] 
14 Jul 22:21:50 ntpdate[7649]: step time server 91.189.94.4 offset 14.057294 sec
 * Starting NTP server ntpd   
root@webserver1:/var/lib/ntp# cat ntp.drift
-104.269

Anything else to look at?

---

### Post by ThomWilhelm on 2010-08-20
For those interested I have changed my ntp.conf on the server connected to the internet to only have one iburst server:

server ntp.ubuntu.com
server pool.ntp.org iburst
server 0.pool.ntp.org
server 1.pool.ntp.org
server 2.pool.ntp.org
server 3.pool.ntp.org
server time.nist.gov
server time-a.nist.gov
server time-b.nist.gov
server time-a.timefreq.bldrdoc.gov
server time-b.timefreq.bldrdoc.gov
server time-c.timefreq.bldrdoc.gov

And this has fixed the problem for me (have been synced perfectly for over 7 days now). ;)

---

### Post by ThomWilhelm on 2010-11-05
Am still having this problem, however it happens less often it seems, I have now pinpointed the problem by looking in my NTP syslog entries:

Nov  5 11:53:59 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 11:54:06 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 11:55:36 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 11:59:05 webserver1 ntpd[3691]: time reset +173.389768 s
Nov  5 11:59:28 webserver1 ntpd[3691]: synchronized to 62.168.65.36, stratum 3
Nov  5 12:02:31 webserver1 ntpd[3691]: synchronized to 193.65.58.57, stratum 2
Nov  5 12:12:23 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 12:14:33 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 12:15:39 webserver1 ntpd[3691]: synchronized to 193.65.58.57, stratum 2
Nov  5 12:18:52 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 12:22:05 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 12:49:58 webserver1 ntpd[3691]: synchronized to 193.65.58.57, stratum 2
Nov  5 13:02:53 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:07:12 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:07:59 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:11:27 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:12:24 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:13:21 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:13:53 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:14:37 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:15:41 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:21:06 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:22:09 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:25:07 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:26:29 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:28:16 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:28:54 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:31:38 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:32:56 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:33:46 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:35:23 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:36:08 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:37:11 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:38:17 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:39:20 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:42:33 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:43:35 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:44:41 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:47:57 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:51:13 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:53:18 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:54:22 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:57:36 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 13:58:40 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 13:59:46 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 14:02:47 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 14:04:56 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 14:09:49 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 14:13:03 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 14:15:40 webserver1 ntpd[3691]: synchronized to 193.55.167.2, stratum 2
Nov  5 14:15:52 webserver1 ntpd[3691]: synchronized to 213.169.37.101, stratum 2
Nov  5 14:19:00 webserver1 ntpd[3691]: time reset +32.799333 s
Nov  5 14:19:27 webserver1 ntpd[3691]: synchronized to 193.65.58.57, stratum 2

Why do I get entries such as:

Nov  5 11:59:05 webserver1 ntpd[3691]: time reset +173.389768 s
Nov  5 14:19:00 webserver1 ntpd[3691]: time reset +32.799333 s

These are the reason my clock is becoming unsyncronised. I have googled but have only found the advice upgrade the OS or your hardware clock is broken. I can upgrade in the future but if anyone has any ideas how I could fix until then that would be helpful!

---

### Post by ThomWilhelm on 2010-12-29
For anyone interested, this was solved by upgrading the server to 10.04 LTS, exactly the same NTP config file and no problems for over a month. :grin:

---

