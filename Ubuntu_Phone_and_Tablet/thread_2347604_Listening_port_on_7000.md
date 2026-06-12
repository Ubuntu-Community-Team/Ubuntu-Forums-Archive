---
title: "Listening port on 7000"
date: 2016-12-27
forum: Ubuntu Phone and Tablet
---

### Post by woody2707-3 on 2016-12-27
Hi All, I have just tried the beta antivirus from open app store on my Bq 5hd and got the above message. I tried the same on Miezu mx 4 and had no issue. Is this anything to worry about?. Both phones are fully updated. As soon as threat is fixed a rescan shows it is back.
Thanks Woody

---

### Post by hosein-iprogramer on 2016-12-28
Hi
An app or script opened 7000 port and it's running in background (maybe, because open ports must be closed after program close like wifi transfer) and antivirus will add this to your firewall , please make sure your firewall is on to secure your device

---

### Post by woody2707-3 on 2016-12-28
Hi, Thanks for the help. Will try and work out what it might be. Firewall showing as active and device secure. Tried it on bq tablet and that was fine as well just the bq phone that seems to have an issue. Nice app though&#128512;

---

### Post by al1u on 2016-12-29
Hi,

to find which program is using this port, use a terminal on your device an enter this :

sudo netstat -pan | grep ":7000"

Normally it should give you the name of the program that is opening this port.

---

### Post by woody2707-3 on 2016-12-29
Hi, Thanks will give it a go. Any idea on how to configure the firewall. Firewall  ufw status is active. Status in the box below states inactive

---

### Post by al1u on 2016-12-29
Hi,

Good question, I checked on my Meizu but it seems that it is not activated too (OTA14), status return inactif, and there is no running process ufw...

---

### Post by woody2707-3 on 2016-12-29
Try running "sudo ufw enable" in a terminal then run "sudo ufw status" and see what you get. Mine came back as active.

---

### Post by woody2707-3 on 2016-12-29
Seem to have fixed listening port issue ran "sudo ufw deny 7000" in a terminal. All appears ok on the bq.

---

### Post by woody2707-3 on 2016-12-30
Latest update still have listening port on 7000. Tried running the above command and got back bash: grep:7000: command not found. Firewall is active and 7000 and 7000(v6) are both deny anywhere. Any other ideas out there&#9786;

---

### Post by al1u on 2016-12-30
Did you use the "" in your command ? : grep ":7000"

---

### Post by woody2707-3 on 2016-12-31
Yes as above
Sudo netstat -pan | grep ":7000"
Will try it again later, can't remember if asked for password after hitting enter then it comes up as not found, or comes up not found then asks for password.

---

### Post by al1u on 2016-12-31
ok, otherwise, try it without the grep like : sudo netstat -pan, you will got the full list of active ports and the program that is openening it.

---

### Post by al1u on 2016-12-31
You normally should be asked for the password as the -p needs higher rights.

---

### Post by woody2707-3 on 2017-01-01
Yes that work on all devices. Will let you know results when have them. So far port has remained closed again.

---

