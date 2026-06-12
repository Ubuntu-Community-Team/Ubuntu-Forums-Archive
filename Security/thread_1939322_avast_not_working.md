---
title: "avast not working"
date: 2012-03-11
forum: Security
---

### Post by colorfultrixe on 2012-03-11
Hi guy and girls I have downloaded avast I managed to installed it.
then I get this error ! an error occurred in avast engine invalid argument/
I went to avast site and followed a fix in terminal and became root ,
sudo su gave my password then put in sysctl -w kernel.shmmax =128000000
Please help I would like to have this on my desktop for ease instead of going into root  please make your reply simple lol :popcorn:

---

### Post by winh8r on 2012-03-11
Open a terminal and enter:

```
avastgui
```

Does it start up in gui mode?

---

### Post by colorfultrixe on 2012-03-11
No hun its doesn't open doing that.
-HP-Pavilion-dv5-Notebook-PC:~$ avastgui

(avastgui:6456): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(avastgui:6456): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(avastgui:6456): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(avastgui:6456): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by colorfultrixe on 2012-03-12
Please can any one help this newbie.
I'm really. Liking Ubuntu and have search the forum
For information on this with no results.
thank you

---

### Post by winh8r on 2012-03-12
I have read through the "fix" on the Avast forum and it seems to be necessary to do the following:

open a terminal

enter the following 

```
gksudo gedit /etc/init.d/rcS
```

now enter the line

```
sysctl -w kernel.shmmax=128000000
```

in the file so that it looks like the example below:

```
Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
#
sysctl -w kernel.shmmax=128000000
exec /etc/init.d/rc S
```

then save the file and close gedit.

run the following:

```
sudo updatedb
```

and according to those guys it should work, I cannot guarantee it because I do not use it.

Hope this helps you.

---

### Post by colorfultrixe on 2012-03-12
OK I have tried what you said and I still have problems.
Dos each code go on its own line
You say in the last post ingedit to save this file ware do I save it to and how should I name this file. Hoping I can get this sorted so I can play in Ubuntu
Thanks Trix):P

---

### Post by winh8r on 2012-03-12
The code you entered should look exactly like it does  in the example in my post above.

it should be on a line of its own, make sure there is no # mark before it as this will cause it to be ignored when the script runs.

to save the edited file in gedit just press control + S and it will save the changes to the file.

You can check that it has been saved by running the first command again and checking.

Hope this helps.

---

### Post by colorfultrixe on 2012-03-12
Still getting the same message
 [COLOR=Red]an error occurred in avast engine invalid argument/[/COLOR] :confused:
have done the code now lots of times I hope it's not causing damage to the file system with doing this it's  a real pain in the butt lol
avast should get this sorted out big time If any one else has any time to help me I sure would be glad of the help.
Thanks Trix

---

### Post by winh8r on 2012-03-12
******WARNING******** This method requires making an alteration to the kernel parameters. It is documented at the AVAST FORUM here:

[http://tinyurl.com/7l6ltff]("http://tinyurl.com/7l6ltff")

Proceed beyond this point at your own risk.

Note down current settings and ensure you have backed up your data.

I am posting this information for information, what you do with it is your choice, there are other alternatives to AVAST available.

If you decide you want to proceed then here is an alternative method to get Avast to start and run.

*********end of warning*****




Run the first command above and remove the line that reads

```
sysctl -w kernel.shmmax=128000000
```

save and close the file as before.

now open a terminal and enter

```
sudo -i
```

then 

```
echo 128000000 >/proc/sys/kernel/shmmax
```

then 

```
exit
```

then launch avast as before

---

### Post by colorfultrixe on 2012-03-12
gee having done all those codes lol. I restarted my computer and after three apptempts to restart I was about to throw lappy out of window when everything had loaded The first codes must have worked. I clicked on avast button and Hey it loaded and scanned part of  puter then everything frooze.
 
Problem solved
 
Thank you so much for all your help:lolflag:

---

### Post by winh8r on 2012-03-12
Glad it worked for you.



Good Luck

---

