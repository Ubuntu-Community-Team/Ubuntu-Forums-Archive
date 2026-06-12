---
title: "Firewall auto-start"
date: 2010-02-26
forum: Security
---

### Post by Advait on 2010-02-26
Hi All,

I have 9.10 running. I'm now in the habit of starting FireStarter and GUFW the first thing after Ubuntu boots. Is there a way to get the firewall to automatically start each time I start Ubuntu?

When I put either gufw or FireStarter in the "Startup" directory, they both ask for a password. Anyway around this?

Thanks,

Tom the Uber Newbie

---

### Post by Enigmapond on 2010-02-26
If you don't want to be bothered by passwords, use neither at start. Just open terminal and type 
```
sudo ufw enable
```

This will start the firewall and set it to start at boot. Firestarter is an old application and you really don't need it. gufw is just a frontend for the firewall and not needed to enable it but is good to set rules.

Cheers!

---

### Post by Revolutionary101 on 2010-02-26
In terminal type this:

```
sudo ufw enable
```

That will start your firewall on startup.

---

### Post by FuturePilot on 2010-02-26
I would recommend not using Firestarter. It's old and unmaintained. Not to mention using two different tools to configure iptables will almost certainly end up in a conflict.

---

### Post by Advait on 2010-02-26
I entered the command. Perfect. Thanks! These Ubuntu forums are terrific. Really helping me learn a lot and getting me quickly comfortable with the world of Ubunutu. I'm a happy newbie...

Cheers,

Tom

---

### Post by Revolutionary101 on 2010-02-26
Glad I could help.

---

### Post by Enigmapond on 2010-02-27
> **Revolutionary101 said:**
> Glad I could help.

Taking credit for repeating what I already told him...:p

I'll let it pass....THIS time....;)

Cheers!

Glad WE could be of help.....

@ OP you should mark the thread as solved in the thread tools...

---

