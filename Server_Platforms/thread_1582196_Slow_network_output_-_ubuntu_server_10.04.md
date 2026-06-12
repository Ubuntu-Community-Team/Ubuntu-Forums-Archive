---
title: "Slow network output - ubuntu server 10.04?"
date: 2010-09-26
forum: Server Platforms
---

### Post by nexuslite on 2010-09-26
This is the current speed issues I have.

Windows Vista WiFi -> Ubuntu Server 10.04, Samba, 2.5MB/s
Ubuntu Server 10.04 -> Windows Vista WiFi, Samba, Choppy Downloads, and Streaming
Ubuntu Server 10.04 -> Ubuntu Desktop, Samba, 700KB/s
Ubuntu Server 10.04 -> Windows Vista WiFi, FTP, 700KB/s
Ubuntu Server 10.04 -> WII WiFi, Samba, Streaming OK

I figure I should be getting similar upload and download speeds which I would like to fix. And the choppy streaming to vista needs to be fixed. I have vista home not pro so I don't have some of the management applications that the fixes suggest. However I had streaming working with a NAS drive which used linux that has recently died the server I am trying to make is to replace the NAS drive.

Any thoughts?

---

### Post by sikander3786 on 2010-09-26
Add this line to the end of your smb.conf's Global Section.

Edit by,
```

sudo gedit /etc/samba/smb.conf

```

and then add this line.

```

read size = 65536

read prediction = true

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

```

Restart Samba

```

sudo service smbd restart

```

And see if it improves.

[COLOR="Red"]**EDIT:**[/COLOR] I have added two more lines to be added. Please update.

---

### Post by nexuslite on 2010-09-26
I knew about the last one but I didn't know about the other two. I think you got something to change but the samba transfer to windows is still very choppy.

Since the issue also affects ftp as far as slow transfer speed and the speeds are identical to ubuntu desktop samba transfers I think there is some server adjustments not related to samba that need to be made. Or is there some wifi issue with transfer speeds that I don't yet know about. I keep thinking I should plug my laptop directly into the router and see if I still have slow download speeds v.s. upload speeds.

---

### Post by nexuslite on 2010-09-26
Okay the speed difference is wifi only I get 12MB/s up and down through FTP while directly connected. I will do some testing on streaming and get back to you as to if that solved my problem.

---

### Post by sikander3786 on 2010-09-26
The slow downs may be caused by ipv6 as well. I am not sure how to turn it off system vide. Wait for someone else with a more accurate answer. I found the following link for Grub2. Might help with Lucid but I am not sure about that. Wait until some one else also recommends it or follow at your own risk.

[http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html)

---

### Post by nexuslite on 2010-09-26
I'm still having the same problem the video dies if streamed over samba and I have to skip around to keep the connection alive to continue the video. I think the biggest issue with streaming is the connection stops working on occasion like samba isn't serving data for just long enough to keep it from doing transfers. I have to click around on directories while i do large file transfers also to keep it alive.

I'm no longer concerned about transfer rates I know they are wifi related.

---

### Post by nexuslite on 2010-09-26
Just to clear up any confusion. A testparm reveals the two following commands aren't samba config instructions.

```


read size = 65536

read prediction = true


```

---

### Post by nexuslite on 2010-09-27
here is more information form the problem these are from the log file at the time the stream stops

```

[2010/09/26 23:35:50,  1] smbd/service.c:1240(close_cnum)
  nexuslite-pc (192.168.0.16) closed connection to service Public
[2010/09/26 23:35:52,  0] libsmb/ntlm_check.c:54(smb_pwd_check_ntlmv1)
  smb_pwd_check_ntlmv1: incorrect password length (68)
[2010/09/26 23:35:52,  0] libsmb/ntlm_check.c:54(smb_pwd_check_ntlmv1)
  smb_pwd_check_ntlmv1: incorrect password length (68)
[2010/09/26 23:35:52,  1] smbd/service.c:1063(make_connection_snum)
  nexuslite-pc (192.168.0.16) connect to service Public initially as user nobody (uid=65534, gid=65534) (pid 5514)

```

I am not using passwords it is all a guest based system.

---

