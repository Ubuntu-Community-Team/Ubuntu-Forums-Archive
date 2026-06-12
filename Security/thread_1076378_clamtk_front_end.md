---
title: "clamtk front end"
date: 2009-02-21
forum: Security
---

### Post by zaphodbblx on 2009-02-21
hey all!
 I was running the clamtk front end untill i realized that it wasnt getting virus signature updates so I uninstalled from the package manager and added just about all the clamtk files I could find from synaptic..most likely not a good move because now the program wont show up. it installs just fine but it just wont run.(from source {clamtk 4.10-1_all.deb} and from synaptic it even shows in the application list)
Not really a big deal honestly because it does work from terminal but I cant figure out how to update the virus database.
 I allways get this message {LibClamAV Warning:database is over 7 days old}..ive tryed a lot of things and nothings working.
antivirus is one place ubuntu is really confounding me! im not really sure how to edit the config or even how to access it and the info out there is VERY confuseing.
any thoughts short of a reinstall?;)

---

### Post by cariboo on 2009-02-21
If you run in a terminal:

```
sudo freshclam
```

it should create a cron job that goes out and checks for updates every day. Check /etc/cron.daily to see if the script has been created.

Jim

---

### Post by binbash on 2009-02-21
you have to stop apparmor if you want to update the signatures.

sudo /etc/init.d/apparmor stop
update signatures now, then
sudo /etc/init.d/apparmor start

---

