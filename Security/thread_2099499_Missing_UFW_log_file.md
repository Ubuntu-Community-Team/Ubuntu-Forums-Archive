---
title: "Missing UFW log file"
date: 2012-12-29
forum: Security
---

### Post by popie on 2012-12-29
I installed UFW on two 10.04 servers. One server is at home, the other is on a data center VPS server.

On the VPS server at data center, the UFW log file does NOT exist in /var/log
However, UFW log entries DO appear in /var/log/messages. 

How can I set my VPS server to log UFW messages to a /var/log/ufw.log file? (seems to be the default on my home server, as this log file exists and contains the UFW messages.)

UFW is configured identically on the two servers, as far as I can tell, and logging is enabled:

$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

Thanks

---

### Post by popie on 2012-12-30
I rebooted the server, and then the ufw.log file appeared... problem solved.

---

### Post by Ms. Daisy on 2012-12-30
Consider installing the free version of [splunk ]("http://www.splunk.com/download")to help you manage the logs you're generating at the data center.

---

### Post by popie on 2012-12-30
> **Ms. Daisy said:**
> Consider installing the free version of [splunk ]("http://www.splunk.com/download")to help you manage the logs you're generating at the data center.

Thanks. Splunk looks interesting, but my vps doesn't meet even the minimum requirements (1GB ram) for installation. Is there another option?

---

### Post by chadk5utc on 2012-12-30
you could look at logwatch its not splunk but works well, easy to configure and will email reports every 24hrs by default.

---

### Post by Ms. Daisy on 2012-12-30
> **chadk5utc said:**
> you could look at logwatch its not splunk but works well, easy to configure and will email reports every 24hrs by default.

Agreed, especially if you don't have many other servers in the company. The nice thing about splunk is that it collects logs from all your servers despite platforms. Not sure if logwatch will aggregate all the logs or treat each box separately.

---

### Post by chadk5utc on 2012-12-30
I believe that it can be configured to sort by hostname if run on a centralized log server but have not had the need or tested this. Splunk would be the better option for data center.

---

### Post by popie on 2012-12-30
Hmmm... Does Logwatch require that I install postfix on my server? Not sure I can tackle that. 

I'm using the UFW defaults, and opened incoming ports for ssh (non-22) and mumble. That's it. Is this good enough?

This server runs only a private mumble / murmer chat. Security is very important to me, but I'm not exactly a linux expert.

Thanks for your help.

---

### Post by cariboo on 2012-12-30
Setting up postfix for use with logwatch is fairly simple, when the configuration screen comes up, just select local delivery, and set your username for the mail to be sent to. Then assuming you don't have a gui on you server, type mail at the prompt. then use the t & d keys to read and delete the emails.

---

### Post by chadk5utc on 2012-12-30
correct me if Im wrong but seems like most linux had some default sendmail setup even for system mail? which logwatch is set for as default"sendmail"

---

### Post by cariboo on 2012-12-30
From apt-cache shwpkg:

```
apt-cache showpkg logwatch
Package: logwatch
Versions: 
7.4.0+svn20111221rev79-1ubuntu1 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages
                  MD5: ece539a8a87c5f861d7f0b865e42a03c
 Description Language: en
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
                  MD5: ece539a8a87c5f861d7f0b865e42a03c


Reverse Depends: 
Dependencies: 
7.4.0+svn20111221rev79-1ubuntu1 - perl (0 (null)) **postfix** (16 (null)) mail-transport-agent (0 (null)) fortune-mod (0 (null)) libdate-manip-perl (0 (null)) 
Provides: 
7.4.0+svn20111221rev79-1ubuntu1 - 
Reverse Provides:
```

Postfix has been a depend of logwatch for several years.

---

### Post by popie on 2012-12-31
Should I install Postfix prior to Logwatch, or since its a dependency will it install automatically?

If I set Postfix to local only, will it have minimal load in my server and have none of the typical mail-server security concerns? 

Will my UFW with default settings suffice? Thanks a lot, and sorry for all the newb questions.. Its my first datacenter server.

---

### Post by chadk5utc on 2012-12-31
> **popie said:**
> Should I install Postfix prior to Logwatch, or since its a dependency will it install automatically?
If I set Postfix to local only, will it have minimal load in my server and have none of the typical mail-server security concerns? 
Will my UFW with default settings suffice? Thanks a lot, and sorry for all the newb questions.. Its my first datacenter server.

I wouldnt think that it would impact your server much at all, and for ufw if mail is local only you wont have to worry there. Not sure what you have for defaults in a data center server?

---

### Post by popie on 2012-12-31
> **chadk5utc said:**
> I wouldnt think that it would impact your server much at all, and for ufw if mail is local only you wont have to worry there. Not sure what you have for defaults in a data center server?

Sorry if that wasn't clear. I was referring to the default settings that ufw provides after installation. That's my primary concern for securing the server. I haven't changed any ufw settings other than opening a couple of incoming ports that I needed.

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

---

### Post by Ms. Daisy on 2012-12-31
Is the database directly facing the internet?

---

### Post by popie on 2012-12-31
Not sure. How would I determine that?

---

### Post by chadk5utc on 2012-12-31
is the database accessed from within the building only or from another state or country? And do you have firewall rule specific for this?

---

### Post by CharlesA on 2012-12-31
> **popie said:**
> Not sure. How would I determine that?

Running:

```
sudo netstat -nlp
```

Should tell you if mysqld is listening on 0.0.0.0 or 127.0.0.1.

> **chadk5utc said:**
> is the database accessed from within the building only or from another state or country? And do you have firewall rule specific for this?

What they said ^.

---

### Post by popie on 2012-12-31
The application is a voice chat server accessed by employees at their homes. My understanding of the database (sqlite) is that its used to verify user names and passwords.

voice chat server: port 8802
ssh: port 2230

Here's the output of netstat -nlp:

```
joe@voice:~$ sudo netstat -nlp
[sudo] password for joe: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2230            0.0.0.0:*               LISTEN      356/sshd        
tcp        0      0 127.0.0.1:6502          0.0.0.0:*               LISTEN      763/murmur    
tcp6       0      0 :::8802                 :::*                    LISTEN      763/murmur    
tcp6       0      0 :::2230                 :::*                    LISTEN      356/sshd        
udp6       0      0 :::8802                 :::*                                763/murmur    
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     1923     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     2545     446/dbus-daemon     /var/run/dbus/system_bus_socket

```

---

