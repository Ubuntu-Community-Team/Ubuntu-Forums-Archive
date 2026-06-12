---
title: "Is ufw protecting my Tablet ?"
date: 2017-05-31
forum: Security
---

### Post by linuxyogi on 2017-05-31
Hi,

I followed [this guide]("https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet") to share connection to my tablet. I am using a WiFi router to share the connection. What I want to know is, is Ubuntu's ufw protecting my tablet ?

---

### Post by #&amp;thj^% on 2017-05-31
It would be best to know if your WiFi router has a built in Firewall.
To find out Google your Wifi router make and model.
And what security method did you use? 
NOTE: WEP for security this is a least secure encryption standard.

---

### Post by linuxyogi on 2017-05-31
> **1fallen said:**
> It would be best to know if your WiFi router has a built in Firewall.
To find out Google your Wifi router make and model.
And what security method did you use? 
NOTE: WEP for security this is a least secure encryption standard.

Yes my router has a built in firewall but its firmware is very old. Its not at all secure for [WAN security]("https://www.cvedetails.com/vulnerability-list/vendor_id-899/product_id-31624/version_id-182671/D-link-Dir-600l-Firmware-2.05.html"). I checked and found that DD-WRT doesnt support my router.
So I want to know is Ubuntu's ufw protecting my Tablet ?

---

### Post by ventrical on 2017-06-02
> **linuxyogi said:**
> Hi,

I followed [this guide]("https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet") to share connection to my tablet. I am using a WiFi router to share the connection. What I want to know is, is Ubuntu's ufw protecting my tablet ?

It would help to know which type of tablet are you using , android, windows, mac. If your tablet is connected to the wii directly , no ufw will not protect. If you are connected to PC (as per your link) then yes , because it protects at root. To verify this your should use gufw so you can monitor reports. You can also set Rules and Profiles to public.

Should look like this.

---

### Post by linuxyogi on 2017-06-02
> **ventrical said:**
> It would help to know which type of tablet are you using , android, windows, mac. If your tablet is connected to the wii directly , no ufw will not protect. If you are connected to PC (as per your link) then yes , because it protects at root. To verify this your should use gufw so you can monitor reports. You can also set Rules and Profiles to public.

Should look like this.

I am using an Android tablet. Its connected to the PC as per that link. My ufw is configured like this 


```
$ sudo ufw status verbose[sudo] password for mypc: 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip



```

---

### Post by #&amp;thj^% on 2017-06-02
> **ventrical said:**
> It would help to know which type of tablet are you using , android, windows, mac. If your tablet is connected to the wii directly , no ufw will not protect. If you are connected to PC (as per your link) then yes , because it protects at root. To verify this your should use gufw so you can monitor reports. You can also set Rules and Profiles to public.

Should look like this.
+1 :)
> **linuxyogi said:**
> I am using an Android tablet. Its connected to the PC as per that link. My ufw is configured like this 


```
$ sudo ufw status verbose[sudo] password for mypc: 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip



```

And maybe check this for yourself: [https://play.google.com/store/apps/details?id=app.greyshirts.firewall&hl=en](https://play.google.com/store/apps/details?id=app.greyshirts.firewall&hl=en)

---

