---
title: "problems to install kerberos on 16.04 server LTS"
date: 2016-10-24
forum: Server Platforms
---

### Post by 2chrism on 2016-10-24
Hello,
i installed a new ubuntu 16.04.1 server LTS and all will be good, IP-Adress, DNS and Samba-installation.
Now i'll to connect from another server to my server , but i get no connection.  I think it will need kerberos on the server. But if i try to install the krb5 there are ever this messages.

Can everyone help me, please?

```
root@server:/etc# sudo apt-get install krb5-kdc krb5-admin-serverPaketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.
Statusinformationen werden eingelesen.... Fertig
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass
Sie eine unmögliche Situation angefordert haben oder, wenn Sie die
Unstable-Distribution verwenden, dass einige erforderliche Pakete noch
nicht erstellt wurden oder Incoming noch nicht verlassen haben.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:


Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 krb5-admin-server : Hängt ab von: libkadm5srv-mit9 (>= 1.12~alpha1+dfsg) soll aber nicht installiert werden
                     Hängt ab von: libkdb5-7 soll aber nicht installiert werden
                     Hängt ab von: libkrb5-3 (= 1.12+dfsg-2ubuntu5.2) aber 1.13.2+dfsg-5 soll installiert werden
 krb5-kdc : Hängt ab von: libkadm5clnt-mit9 (>= 1.12~alpha1+dfsg) soll aber nicht installiert werden
            Hängt ab von: libkadm5srv-mit9 (>= 1.12~alpha1+dfsg) soll aber nicht installiert werden
            Hängt ab von: libkdb5-7 soll aber nicht installiert werden
            Hängt ab von: libkrb5-3 (= 1.12+dfsg-2ubuntu5.2) aber 1.13.2+dfsg-5 soll installiert werden
            Hängt ab von: krb5-user soll aber nicht installiert werden
E: Probleme können nicht korrigiert werden, Sie haben zurückgehaltene defekte Pakete.
```

regard
Chris

---

### Post by howefield on 2016-10-24
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by 2chrism on 2016-10-25
OK, i solved my problem.
i think it will be better to take the original source.list in the (etc/apt/source.list), then it will work everyting better. :)

Regards
Chris

---

