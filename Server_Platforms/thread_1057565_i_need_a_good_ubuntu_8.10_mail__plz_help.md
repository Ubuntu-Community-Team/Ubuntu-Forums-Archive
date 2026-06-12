---
title: "i need a good ubuntu 8.10 mail ? plz help"
date: 2009-02-01
forum: Server Platforms
---

### Post by sfuller on 2009-02-01
first iwhat to say that for all you help! i folower Dr.Small post and it help a lot put when i run this command
sudo dpkg-statoverride --force --update --add root sasl 755 /var/spool/postfix/var/run/saslauthd
i get directory no such file or directory if i make it it tell me
force will be ignored and no matter what it do when i start or restart saslauthd iget /ect/default/saslauthd:8:PWDIR: not found
here is my /ect/default/saslauthd
START=yes
**_[COLOR="Red"]this is line 8>[/COLOR]_**PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd" and i followed this example [http://ubuntuforums.org/showthread.php?t=990582](http://ubuntuforums.org/showthread.php?t=990582) 
      
i am run ubuntu 8.10 with no GUI i just need a server i remote login  to i was flurdy's but i dont need all of that plus i dont realy know mysql

---

### Post by sfuller on 2009-02-02
could anyone help i am wiil to try anything even changing os .

---

### Post by Neural oD on 2009-02-02
what exactly are you looking for - a gui-less mail clien?

---

### Post by sfuller on 2009-02-02
> **Neural oD said:**
> what exactly are you looking for - a gui-less mail clien?
  
sorry not a gui less mail clint my current server is gui less sorry

---

### Post by Neural oD on 2009-02-02
so can you specify what it is that you are looking for - as I'm not clearly understanding what it is that you require

---

### Post by sfuller on 2009-02-02
> **Neural oD said:**
> so can you specify what it is that you are looking for - as I'm not clearly understanding what it is that you require

yes i want a amil server that user can remote into from out side the network i have try all the guides on the forum and can never get sasl right i used DR small that  guide like i said but i changed the PWDIR like i said above i think ever thing else is right in the guide put cant get past it so i gusee it time to reformat and start again

---

### Post by Neural oD on 2009-02-02
well a good mail program I use is postfix - but there are many out there. I would suggest looking at the postfix website - or the site of the mail software that you choose. These would be the correct places to start, and they should have good guides for setting such things up and for configuring them.

---

### Post by sfuller on 2009-02-02
> **Neural oD said:**
> well a good mail program I use is postfix - but there are many out there. I would suggest looking at the postfix website - or the site of the mail software that you choose. These would be the correct places to start, and they should have good guides for setting such things up and for configuring them.
i am runing postfix i can not get sasl working?

---

### Post by Poleh on 2009-02-02
> **sfuller said:**
> i am runing postfix i can not get sasl working?

I suggest you take a look at this link below - yes it is for 7.10 but it is still applicable for 8.x and talks about setting up SASL and IMAP.

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

