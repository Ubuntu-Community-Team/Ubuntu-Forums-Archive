---
title: "ufw"
date: 2010-05-27
forum: Server Platforms
---

### Post by whitetimer on 2010-05-27
Hi All

I have Xubuntu as my host with ubuntu server as guest on virtualbox.  I have just installed webmin, but i dont seem to be able to connect, so what ports do i need to open in ufw to allow me to connect ?

Many Thanks
:guitar:

---

### Post by spynappels on 2010-05-27
Have you enabled iptables? This is not enabled by default, so unless you enabled it yourself, it should not be causing you problems. If you have enabled it, you need to allow requests in on port 10000.

Remember you also need to specifiy the port when you try to access Webmin:

[https://your-lan-ip:10000](https://your-lan-ip:10000)

and you should receive a certificate warning which you will have to accept and then you will be able to access the login page.

---

### Post by whitetimer on 2010-05-27
> **spynappels said:**
> Have you enabled iptables? This is not enabled by default, so unless you enabled it yourself, it should not be causing you problems. If you have enabled it, you need to allow requests in on port 10000.

Remember you also need to specifiy the port when you try to access Webmin:

[https://your-lan-ip:10000](https://your-lan-ip:10000)

and you should receive a certificate warning which you will have to accept and then you will be able to access the login page.

Yes i have iptables enabled and just forgot to allow port 10000 ... duh

Many Thanks for the reminder :)

---

### Post by terazen on 2010-05-27
I use `sudo netstat -nap | grep -i listen` and look for the ports the server is listening on for a particular process.

---

