---
title: "RSA ssh keys"
date: 2012-01-11
forum: Security
---

### Post by Drenriza on 2012-01-11
Im in a situation where i administrate multiple servers (in the hundreds) and have created a script, that allow all my servers to download specific files at a central server. But how can i ensure with RSA keys that people cant just go into my script (vim it) and see what server the script is using.

example of command i use to download different files.
scp -r server1:/files .

I also use ssh to execute commands on the central server to build up the files that should be
downloaded. Since its done from user input (variables)

ssh -f server1 "command"

But here users would read that my server is server1 and rsa works over ssh they can just connect to it and make trouble.

So is their a way to mask the server1 ip? Get the script to get the string on a hidden place on the local system that normal users cant figure out or what can you do?

Hopes it makes sense.
If it docent, please don't hesitate to say so.

Thanks on advance.
Kind regards.

---

### Post by Lars Noodén on 2012-01-11
You can make the keys [single purpose](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Key-based_Authentication#Single-purpose_keys).  When you have them in [font=Courier New]authorized_keys[/font] add [font=Courier New]command=""[/font] to the beginning of the key and put your command between the quotes.

So

```

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCpT+hQ9p364auRMIgrdaUOvU0TOU4FU50BqtKEwkvisvY/vl5uNW7DLXxEP+lR26RtAx81N10FarumZRwiIpFNwa8S7UJgAqXtnqLARuX1aHsdNmrRzUMCRsqEnBdomD/q2aiu8WLJCqExwDDwRihepe9nuT0zfi2FAzo16zBT1xFF3uhkKXYKWEH9AkSyq7sLJB+Q2JW2RnyGVNRf0XJCtOni4ybSP/PSCOcprsrhhkXNbzj5iP+ORNo0UfFyJLDmsAIMtq6NG0VG06PC1A4i3B8eqEGOiV22i5FMLi0wvEqQzkwnDve1rvD4MF5L4T/9yPZLbRCTT7TKzufbej/L

```

becomes

```

command="/usr/local/bin/*somescript*" ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCpT+hQ9p364auRMIgrdaUOvU0TOU4FU50BqtKEwkvisvY/vl5uNW7DLXxEP+lR26RtAx81N10FarumZRwiIpFNwa8S7UJgAqXtnqLARuX1aHsdNmrRzUMCRsqEnBdomD/q2aiu8WLJCqExwDDwRihepe9nuT0zfi2FAzo16zBT1xFF3uhkKXYKWEH9AkSyq7sLJB+Q2JW2RnyGVNRf0XJCtOni4ybSP/PSCOcprsrhhkXNbzj5iP+ORNo0UfFyJLDmsAIMtq6NG0VG06PC1A4i3B8eqEGOiV22i5FMLi0wvEqQzkwnDve1rvD4MF5L4T/9yPZLbRCTT7TKzufbej/L

```

---

### Post by Drenriza on 2012-01-11
If i make a single-purpose RSA key, and use that in my script. How does that hold-back users. Using the RSA key to connect to the remote server, that the script is using?

---

### Post by Lars Noodén on 2012-01-11
It means that they can only use that key for one single operation and that operation is carried out automatically when they connect.  

If you want to avoid typing the passphrase again and again, then use an agent.

---

