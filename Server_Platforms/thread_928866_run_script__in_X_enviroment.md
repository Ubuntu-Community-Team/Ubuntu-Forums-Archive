---
title: "run script  in X enviroment"
date: 2008-09-24
forum: Server Platforms
---

### Post by alasarr on 2008-09-24
Hello!

I've application (which start with a bash script) in c++ which works with a gui, but I don't use this gui...(in the gui the user only specifies the parameters but for me the defaults parameters are good). Now I've install xubuntu in my server so when I start xubuntu and start the script all work fine...

I want to start this application every time at boot. I've trying insert a call in rc.local but the application say "cannot connect to X server"...so how could I start my script  with X???

I know it's not a good idea...but I need to do this

thank you, and sorry about the english

---

### Post by kerry_s on 2008-09-24
look in your menu, there should be a autostart program.

---

### Post by prshah on 2008-09-24
> **alasarr said:**
> Now I've install xubuntu in my server 
I want to start this application every time at boot. 


You can add it to your Applications-System-Autostarted Applications list. (Xubuntu)

---

### Post by cariboo on 2008-09-24
Put your script in /etc/init.d, then run update-rc.d. For more on update-rc.d:

```
man update-rc.d
```

Jim

---

### Post by alasarr on 2008-09-25
> **prshah said:**
> You can add it to your Applications-System-Autostarted Applications list. (Xubuntu)

It work fine! I didn't know how to xubuntu session started auto...so I've auto started ubuntu and I've added my script in Autostarted Appiclation list!

Thank you very much!!

---

