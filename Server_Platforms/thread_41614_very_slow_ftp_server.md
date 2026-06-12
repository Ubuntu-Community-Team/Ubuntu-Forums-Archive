---
title: "very slow ftp server"
date: 2005-06-14
forum: Server Platforms
---

### Post by salihburhan on 2005-06-14
I set up a vsftp. The server is extremely slow. My connection is 256 kb adsl. It takes hours to download a 700 KB file  from the server. My previous server was a proftp in Debian with the same problem. I checked the connection speed and it seems OK. The ftp server is very fast in the intranet. And the clients using the server from outside can surf the web quite fast. 

Could someone please tell me where the problem could be? My network is pretty small (15 PCs using only sql) so there would be no bottlenecks anywhere.. The only alternative maybe is the adsl modem/router. (I know this is not directly related to Ubuntu.)

---

### Post by LordHunter317 on 2005-06-14
It's a network issue, likely QoS related, and without more network details there's no way to tell.

---

### Post by salihburhan on 2005-06-14
What kind of details? As I said, the ftp server on Ubuntu is very fast when connect from a PC inside the LAN. I have a ADSL modem that acts as a gateway. 

by the way, what is a QoS (quality of service?)? My ISP checked out my connection and tells me that it is absolutely normal..

---

### Post by LordHunter317 on 2005-06-14
QoS refers to technology that allows you to control the priority for traffic to be sent out over a link.

It's potentially your ASDL modem.  What's the connection you tested from?  How did you test?  Was there any other Internet traffic on either LAN?

---

### Post by salihburhan on 2005-06-14
I called the modem (zoom adsl X5) company they said that the modem does not have any setting for setting priorities (my modem is also my router). Then I called my ISP. They said everything seems fine. I tested from both another adsl connection and also another dialup connection. It is awfully slow. The speed test of my isp (web based) shows that download is OK. Their upload test does not work &<.. So I tried another upload test from some server in the US (I am in Turkey). Both the upload and download are slow.. There is probably a bottleneck going out of Turkey anyway.. 

There is no upload traffic inside my LAN. Even if there is, it seems not right that a 700 KB file takes ages and usually gives a timeout. 

I conclude that somehow the ftp server (vsftp) responds fast for the LAN and is somewhat slow responding to the WAN. It is either because of the modem (the modem company is lying) or the server or the connection (the isp is lying). This stpid thing is sooo frustrating.  

I am just wondering if the server can in some way slow down or if the adsl modems (pretty straightfoward mdoem nothing fancy) may have a setting for bandwidth.

Thanks a lot..

---

### Post by LordHunter317 on 2005-06-14
Your conclusion is flawed.  However, to verify it's not the modem or another issue, go check the speed tools as dslreports.com.

If you tested on dialup, you're not going to see a speed faster then the download speed of the dialup.  You're always constrained by the smallest pipe on the path.  So your test is flawed.

If there's other traffic being sent out, it would be perfectly reasonable for your FTP to be terribly slow and or timeout.

---

### Post by salihburhan on 2005-06-14
I did the bandwidth test from inside the lan. My test with the dialup was to see the speed of the ftp server from outside the lan (web browsing was fairly fast as opposed to the ftp connection). Actually, I did the speed test from the web page you mentioned. The only traffic that is worth mentioning is download. We do not upload anything except the ftp server we have. The server serves only 4 people who download the same file. 

Does a big download traffic affect the upload.? My upload and download have seperate bandwidths.

---

### Post by LordHunter317 on 2005-06-14
[QUOTE=salihburhan] My test with the dialup was to see the speed of the ftp server from outside the lan (web browsing was fairly fast as opposed to the ftp connection). [/quote]Right, and you saw crappy speeds because you were limted by the download connection.

> Does a big download traffic affect the upload.? My upload and download have seperate bandwidths.Yes, it can.  You have to send ACKs in response to downloaded files.

Post the results from dslreports.com.

---

