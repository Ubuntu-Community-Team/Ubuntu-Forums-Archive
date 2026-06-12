---
title: "Firestarter Startup"
date: 2007-01-29
forum: Server Platforms
---

### Post by weaver4 on 2007-01-29
I am a newbie.

I need a firewall so I got downloaded firestarter and got it set up...pretty slick.  But when I reboot my computer it does not run automatically.  

How do I get it set up so it will run when I reboot?

Thanks,

---

### Post by ciscosurfer on 2007-01-29
> **weaver4 said:**
> I am a newbie.

I need a firewall so I got downloaded firestarter and got it set up...pretty slick.  But when I reboot my computer it does not run automatically.  

How do I get it set up so it will run when I reboot?

Thanks,You can put a reference to it from within your startup sessions tab.  Go here: System > Preferences > Sessions, click Startup Programs, Add, type in **gksu** **firestarter**, click OK, close Sessions.  Log out, log back in.  :-)

---

### Post by weaver4 on 2007-01-29
Thanks,

Will that make Firestarter run even if I do not log in?  I want it to run whenever the machine reboots even if I or no one else logs in.

---

### Post by ciscosurfer on 2007-01-29
> **weaver4 said:**
> Thanks,

Will that make Firestarter run even if I do not log in?  I want it to run whenever the machine reboots even if I or no one else logs in.I would suggest taking a look [at the documentation]("http://www.fs-security.com/docs.php") first, to get a run-down of how to use it.  Keep in mind, though, that Firestarter was created as a graphical front-end to ipchains or iptabes, to allow ease of use and administration on a desktop.  What I'm saying is that if you aren't going to log in as a user and start X, then running Firestarter seems pointless.  You can administer iptables from the command line (you'd still need to log in though).  

That being said, an easy way to modify startup processes is to go into an app called bum (you need to download it):```
sudo aptitude install bum
```and check the Advanced checkbox at the bottom, click on over to Startup Processes and modify away.  Be careful!!

---

### Post by weaver4 on 2007-01-29
Once Firestarter has built the tables I just want them to be executed at startup.

I think it is rather silly to have a program that calles itself a firewall program that doesn't automatically start the firewall when it re-starts.

---

### Post by jrock2004 on 2007-01-29
it is a front end. It still requires iptables. It sets up iptables so you dont need the code. firestarter is not the firewall at all

---

### Post by weaver4 on 2007-01-29
Maybe I am asking the wrong question.  Once I use firestarter will the firewall be running when I reboot?  Or do I need to run firestarter to get the firewall to work?

---

### Post by ciscosurfer on 2007-01-30
> **weaver4 said:**
> Maybe I am asking the wrong question.  Once I use firestarter will the firewall be running when I reboot?  Or do I need to run firestarter to get the firewall to work?Your questions are understandable if this is the first time you are working with iptables and front-ends to said app.  Basically, Firestarter is essentially supposed to be used in a graphical environment.  But as I said before, you *can* use it strictly on the command line w/out using a GUI.  I would suggest reading the man pages on iptables to get a better understanding of how it works and how to make the best use of it.  You can issue the following from the command line to get more info on iptables```
man iptables
```

---

### Post by meng on 2007-01-30
weaver: the simple answer to your question (as stated by jrock) is that you don't need to have firestarter running for the firewall to be active. Firestarter just modifies the firewall settings. The firewall is active by default.

---

### Post by PartisanEntity on 2007-02-01
> **meng said:**
> weaver: the simple answer to your question (as stated by jrock) is that you don't need to have firestarter running for the firewall to be active. Firestarter just modifies the firewall settings. The firewall is active by default.

Thank God someone finally gave the poor chap the straight forward answer, what a way to make people warm up to Linux and Ubuntu... :roll:

---

### Post by glabouni on 2007-02-01
to know if firestarter is up and running use this command
```
sudo /etc/firestarter/firestarter.sh status
```

replace status with start to start firestarter, with stop to stop it and with restart to stop and start it one command.

---

