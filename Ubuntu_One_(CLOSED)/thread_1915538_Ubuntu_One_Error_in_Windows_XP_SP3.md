---
title: "Ubuntu One: Error in Windows XP SP3"
date: 2012-01-26
forum: Ubuntu One (CLOSED)
---

### Post by aldakur on 2012-01-26
Hello!

This is my problem in Windows XP SP3

"NoType  object has no attribute get_rootdir"

Thank You!


[IMG]http://a7.sphotos.ak.fbcdn.net/hphotos-ak-ash4/s720x720/426361_375350505814545_100000187966941_1745865_71215508_n.jpg[/IMG]

---

### Post by duanedesign on 2012-01-26
HI,
Could you please try the folowing:

1. Quit the Ubuntu One application

2. Right-click on the task bar and select "Task Manager"

3. In "Task Manager", click on the "Processes" tab

4. Click on any entries that start with "ubuntuone" and then click the
"End Process" button (If a window pops up prompting you to reinstall
Ubuntu One, click the windows' "Cancel" button)

5. Open the file explorer and make sure you can view hidden/system folders

6. Open C:\Users\yourusername\AppData\Local\xdg\ubuntuone

7. Delete the "syncdaemon" folder

8. Open the Ubuntu One application and connect

Thanks,
Duane

---

### Post by aldakur on 2012-01-31
I'm sorry but does not work

---

### Post by duanedesign on 2012-02-02
Are you using Ubuntu One behind a proxy? Currently U1 does not have proxy support...but we are getting close :)

---

### Post by webercalixto on 2012-02-15
I also have the same problem under XP SP3.

Anyone can help?

---

### Post by CivilizationII on 2012-02-17
If the software doesn't work, you can access your file via your browser login  on ubuntu one. Not really fancy but could save the day.

---

