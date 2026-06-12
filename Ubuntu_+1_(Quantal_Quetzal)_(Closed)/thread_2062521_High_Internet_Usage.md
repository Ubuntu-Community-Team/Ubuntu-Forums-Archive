---
title: "High Internet Usage"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by chrismine on 2012-09-25
For I while now I have seen that my Internet usage has been very high, according to System Monitor have already done 136MB since booting - uptime 50 minutes.

Only web browsing done since reboot.

Can somebody point me to steps or utilities to point me to which specific program is doing this?

Thank you.

---

### Post by TenPlus1 on 2012-09-25
Web sites are becoming larger as the bandwidth increases and I can believe that 50 mins of web surfing would result in 136mb of data downloaded...  To decrease this number try installing a few addon's like Adblock and Flashblock...

---

### Post by chrismine on 2012-09-25
That may be true but not when the computer stands idle with no web browser open and I can see via taskmonitor how the network use data...

This has been happening only for the last month...

---

### Post by dino99 on 2012-09-25
you might watch your syslog into /var/log/ to know about communication, and maybe review your firewall settings. Have you installed a tool like pgl to get protection ? 
([https://launchpad.net/~jre-phoenix/+archive/ppa](https://launchpad.net/~jre-phoenix/+archive/ppa))

---

### Post by rai4shu2 on 2012-09-25
Probably just apt-get update running in the background. You know, each update is like about 20MB for 12.04, so it must be huge for 12.10.

---

### Post by chrismine on 2012-09-25
Thank you - have stumbled upon it by accident - it is Thunderbird (Daily) synchronizing with my gmail account. Don't know what changed in the meantime but made some changes in synchronizing settings, will check...

I have never used more than 35GB a month now already up to 61GB.

35GB used up by the 10th already....

---

### Post by SlugSlug on 2012-09-25
iftop 

is quite useful

---

### Post by cariboo on 2012-09-25
I always lsof to check where my system is connecting to when it is running. Try:

```
sudo lsof -i -P -n
```

These are the relevant connections on my system right now:

```
ubuntu-ge 2205 cariboo   11u  IPv4  12168      0t0  TCP 192.168.0.10:58145->91.189.94.25:80 (CLOSE_WAIT)
unity-sco 2317 cariboo   12u  IPv4  84126      0t0  TCP 192.168.0.10:44773->91.189.89.134:80 (CLOSE_WAIT)
chromium- 2957 cariboo   70u  IPv4  68952      0t0  TCP 192.168.0.10:46922->173.194.33.36:443 (ESTABLISHED)
chromium- 2957 cariboo   90u  IPv4  18581      0t0  TCP 192.168.0.10:37435->74.125.141.125:5222 (ESTABLISHED)
```

You can check the ip addresses using whois from the command line.

**Note:** whois isn't installed by default any more.

---

### Post by chrismine on 2012-09-25
Thanks cariboo907 thats what I am looking for. Did 1.2gb yesterday...

---

### Post by VinDSL on 2012-09-25
> **cariboo907 said:**
> I always lsof to check where my system is connecting to when it is running.
I'm a 'netstat' fanboi.  :D

It's very flexible!

This should give a clue...

```
netstat -p -c
```

---

### Post by sharathkumar on 2012-09-25
An hour of browsing is enough to eat up 150MB. So, don't worry.

---

### Post by chrismine on 2012-09-26
I am very worried - it is not the Internet usage, I made a little experiment this morning:
On startup of Thunderbird it check the gmail Inbox - 14MB gone...
I emptied the inbox by deleting some messages and moving some to other folders - it uses 2MB just to check for new messages - there were none. Do this every ten minutes for a whole day and I am getting very worried indeed....
If there is messages and it uses 14MB every 10 minutes....    not good>

Any pointers as to this most welcome.


I am posting in quantal forums as it is what I am on, also using Thunderbird-trunk (Daily) from the repo's...

---

### Post by jerrylamos on 2012-09-26
Are you using any of the Unity/compiz/lens features?  Seems to me from Shuttleworth's comments there might be a lot of inernet usage for the "everything for everybody all the time" goals.

Obviously I don't know what's coming since I can hardly even grasp what's going on now.  

My service here is relatively cheap no quantity limit that I've hit but just 1.5 mb/s so I just wait.

BTW for mail I use Yahoo, AOL, Gmail since I've got 3 pc's and may do mail from my wife's two pc's or my son-in-law's pc or my daughter's pc, so my mail is equally available from all of them.  I can't comment on Thunderbird.

---

### Post by chrismine on 2012-09-26
Fortunately I am one of the lucky few in South Africa with a 10Mbps ADSL connection....
Not uncapped but I have never used 61GB like this month, I alsways come through with about 35GB - something changed somewhere...

I am monitoring it as follow:
1. No programs open.
2. Open System Monitor
3. Check network history total received
4. Open Thunderbird - see 3MB added to total received - line so fast it takes about 10 seconds.
5. This happens with empty inbox and no mail coming in
6. Thunderbird use 3MB just to check for mail...

BTW it is set up with IMAP...

I also have three other accounts setup but I can see from Thunderbird progress bar bottom right it is when checking the gmail account that it happens...

What the heck....

---

### Post by jerrylamos on 2012-09-26
Be interesting to see what happens to your internet traffic when Amazon and other unity shopping lens built in features get going.  Is the target market 4G?

---

### Post by rai4shu2 on 2012-09-26
We don't even have delta debs, so you can bet this distro is aimed at broadband unlimited users pretty much exclusively.

---

### Post by vasa1 on 2012-09-26
> **rai4shu2 said:**
> We don't even have delta debs, so you can bet this distro is aimed at broadband unlimited users pretty much exclusively.
I didn't even think of using Linux until I could have uncapped internet usage (even if it's a very modest speed).
The only "deltas" I'm aware of are from Firefox and Seamonkey, when installed **direct** from Mozilla.

---

### Post by cariboo on 2012-09-27
I personally think it may be a different problem that chrismine is suffering from, even though my usage hasn't changed this month, I've used less bandwidth so far this month, than I have the last three months.

All of that are saying bandwidth usage is higher, do you actually have proof, or is this specualation?

---

### Post by vasa1 on 2012-09-27
> **cariboo907 said:**
> I personally think it may be a different problem that chrismine is suffering from, even though my usage hasn't changed this month, I've used less bandwidth so far this month, than I have the last three months.
...
@Cariboo907, please could you share how to monitor bandwidth usage the way you illustrated? Perhaps in another thread?

---

### Post by lisati on 2012-09-27
> **vasa1 said:**
> @Cariboo907, please could you share how to monitor bandwidth usage the way you illustrated? Perhaps in another thread?

Some ISPs allow you to log in to an account page where you can get a day-by-day breakdown of usage. Sadly, the graphics provided by the ISP I use are't quite so nice, but the information is still available. :(

---

### Post by vasa1 on 2012-09-27
> **lisati said:**
> Some ISPs allow you to log in to an account page where you can get a day-by-day breakdown of usage. ...
How true! I missed the obvious solution :)

---

### Post by chrismine on 2012-09-27
Now checking mail on ASUS TF300TG tablet pc....

If it uses as much data I don't know about it yet....

---

### Post by cariboo on 2012-09-27
> **vasa1 said:**
> @Cariboo907, please could you share how to monitor bandwidth usage the way you illustrated? Perhaps in another thread?

The graphic is from my account page, with Shaw Communications, unfortunately they are Canadian only.

---

