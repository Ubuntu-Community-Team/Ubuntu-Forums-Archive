---
title: "Logwatch Install Help"
date: 2013-08-01
forum: Server Platforms
---

### Post by lingpanda on 2013-08-01
I installed logwatch on my mail server using this guide. [https://library.linode.com/server-monitoring/logwatch/ubuntu-12.04-precise-pangolin](https://library.linode.com/server-monitoring/logwatch/ubuntu-12.04-precise-pangolin). All is well on this server but when I attempt to install on my samba4 DC server it will not send email. I assume my Postfix configuration is not correct. What steps can I take to debug? Thanks.

---

### Post by CharlesA on 2013-08-01
Check to see if you can actually send mail from the Samba 4 box.

```
echo "Testing" | mail -s "Testing" email@host
```

---

### Post by lingpanda on 2013-08-02
> **CharlesA said:**
> Check to see if you can actually send mail from the Samba 4 box.

```
echo "Testing" | mail -s "Testing" email@host
```

I was not able to receive this test email. I was flagged to install mailutils to run this command. I can send a message to root using

```
echo "Testing" | mail -s "Testing" root@dc.mydomain.com
```

---

### Post by CharlesA on 2013-08-02
OK, make sure postfix or whatever server you are using to send mail is set up correctly. It looks like it might be set to send mail locally only.

You could try running this:

```
sudo dpkg-reconfigure postfix
```

---

