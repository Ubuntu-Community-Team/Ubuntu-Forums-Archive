---
title: "Anyone running a twiki?"
date: 2006-06-20
forum: Server Platforms
---

### Post by Aximilli on 2006-06-20
I have my server running apache correctly, but I can't figure out how to get twiki up and running. Are there any noob-friendly howto's out there? or possibly anyone running a twiki with some good advice?

---

### Post by tjb4u on 2006-07-31
If anyone is interested I have posted some instructions on how to get TWiki up and running on Ubuntu Server. Being a Linux newbie I struggled for a while to get it up and thought others might be interested in a more detailed instructions on how to do the same:
[LIST]
[*][ HOWTO: Install TWiki 4.0.4 on Ubuntu Server 6.06 LTS]("http://ubuntuforums.org/showthread.php?t=219213")
[/LIST]

---

### Post by verbatim210 on 2006-07-31
sorry to lead this topic astray, but do you know wikipedia...
i was just wondering, can those documents be edited free by the public?

like for example someone could just come along and mess up all the documents by editing everything

---

### Post by Socratez on 2006-08-01
I think they can be ... If you want to see a interesting evolution of a Wikipedia page download the GreaseMonky Extention for Firefox ... It will go back through the revisions and show the evolution of the page ...

---

### Post by Cato2 on 2007-11-14
Here is a much easier way to install TWiki - tested on Feisty and Gutsy, and should work on earlier versions as well.  See the [TWiki on Ubuntu HOWTO]("http://twiki.org/cgi-bin/view/Codev/TWikiOnUbuntu") page at TWiki.org for details.  

Hint: the most complicated part of this installation is finding the 'apache2' and 'twiki' packages in Synaptic, or just typing ```
sudo apt-get install apache2 twiki
``` :)

---

### Post by ubunata on 2007-11-17
I know twikis are used on servers, but can i use one for my laptop?... My need is to have complete track of what i search and use from the internet. and work too..

---

### Post by Cato2 on 2007-11-19
> **ubunata said:**
> I know twikis are used on servers, but can i use one for my laptop?... My need is to have complete track of what i search and use from the internet. and work too..

Absolutely - I use a TWiki at home to keep track of all sorts of domestic stuff, as well as notes on Linux/Windows setup, PC/network stuff, research before buying gizmos, etc.  It's on a desktop PC but you can also run TWiki on laptops - I installed it on Xubuntu Gutsy on an old laptop and it works very nicely.

You can even install TWiki on a USB key and take it around different Windows PCs to use it there (with a lightweight webserver).  This is not a bad way to carry around the data from your Ubuntu laptop TWiki incidentally - just use Unison (in the Ubuntu repositories) to do 2-way syncing of the TWiki data (in your 'data' and 'pub' directories) between USB stick and your laptop.  Then you can make changes on a Windows PC when out and about, and resync when you get back to your laptop.

If you only want to do a backup (one-way sync), just do something like this from your TWiki directory, as here:

```
cd /var/lib/twiki
rsync -avz pub data /media/my_usb_stick/twiki 
``` 

This is simpler if you always have your laptop with you and just need a backup.

---

### Post by ubunata on 2007-11-20
cato2:

thanks for the info... helpful for sure... :)

---

### Post by Jarthur911 on 2007-11-20
Hi I've just installed Twiki on a Gutsy Server and it works great except you can't configure the site or add users without the admin password. Anyone know what it is?

---

### Post by Cato2 on 2007-11-21
> **Jarthur911 said:**
> Hi I've just installed Twiki on a Gutsy Server and it works great except you can't configure the site or add users without the admin password. Anyone know what it is?

I just checked on my TWiki laptop (Gutsy) - the default seems to be user TWikiGuest, password guest. If you do 'aptitude install apache2 twiki' as recommended in the TWikiOnUbuntu page at TWiki.org, you will be prompted to specify a suitable password for this userid.  See [Step 3 of the TWiki.org HOWTO on installing TWiki on Ubuntu]("http://twiki.org/cgi-bin/view/Codev/TWikiOnUbuntu#Step_3_Install_Apache_and_TWiki").

However, if you installed through Synaptic, Adept or Add/Remove, it's possible you didn't see this prompt at all.

If you can't remember the password you can reset it from command line as follows:
```
sudo -u www-data htpasswd /var/lib/twiki/data/.htpasswd TWikiGuest

```
Then just type the new password that you want. 

It's best to create a new TWikiAdmin user, as well as a password for 'configure' - see the docs on your own TWiki in the TWiki web, to see how to do that.  Also the Main web has some useful topics that are fairly clear.  However that's not essential if you are trying out TWiki - just put TWikiGuest in the TWikiAdminGroup by editing the [Main.TWikiAdminGroup]("http://localhost/cgi-bin/twiki/view/Main/TWikiAdminGroup") page on your TWiki, following instructions there.

Could you let me know how you installed TWiki?  Via Synaptic or some other GUI perhaps?  This will help in updating the TWikiOnUbuntu HOWTO at TWiki.org.

---

