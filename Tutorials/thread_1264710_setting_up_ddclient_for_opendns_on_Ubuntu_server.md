---
title: "setting up ddclient for opendns on Ubuntu server"
date: 2009-09-12
forum: Tutorials
---

### Post by nucleuskore on 2009-09-12
Hi everyone
As a member of our library committee for the year 2009-2010, I was entrusted the task of helping out IT department in setting up a proxy for the purpose of filtering and regulating web traffic in our computer library. While I did not face any problem in setting up squid (non-transparent mode) on Ubuntu server 8.0.4.2 using the tutorials in ubuntugeek, I had hell on earth trying to get ddclient to work. This was compounded with the availability of incomplete documentation (?) on the opendns website, and conflicting examples in various fora. Hence this short tutorial :)


#To install packages for ssl communication in perl. This is required for authentication.
In the terminal type

**sudo apt-get install libio-socket-ssl-perl**

and press ENTER, press Y when prompted and press ENTER.

#Download ddclient
Download ddclient 3.8.0 from [http://ddclient.sourceforge.net](http://ddclient.sourceforge.net) or from [here](http://www.zshare.net/download/654620026f700b39/)

#Unpack the tarball
**tar xvf ddclient-**

and press TAB to auto complete. Press ENTER.

#Navigate to extracted folder
**cd ddclient-**

and press TAB to auto complete. Press ENTER.

#List contents
**ls**
and press ENTER. This is what you see

Changelog                   sample-etc_cron.d_ddclient
ChangeLog                   sample-etc_ddclient.conf
COPYING                     sample-etc_dhclient-exit-hooks
COPYRIGHT                   sample-etc_dhcpc_dhcpcd-eth0.exe
ddclient                    sample-etc_ppp_ip-up.local
README                      sample-etc_rc.d_init.d_ddclient
README.cisco                sample-etc_rc.d_init.d_ddclient.lsb
README.ssl                  sample-etc_rc.d_init.d_ddclient.redhat
RELEASENOTE                 sample-etc_rc.d_init.d_ddclient.ubuntu
sample-ddclient-wrapper.sh  TODO

#Copy the dd client executable to system binary folder
**sudo cp ddclient /usr/sbin/**

#Make required directories as root for further installation
[B]sudo mkdir /etc/ddclient
sudo mkdir /var/cache/ddclient[/B]

#Copy the files to their destination
**sudo cp sample-etc_ddclient.conf /etc/ddclient/ddclient.conf**

#Editing the configuration file
**sudo vi /etc/ddclient/ddclient.conf**

Some of the changes you are going to make now are optional.

Daemon updates ip every 300 seconds. Change value if desired.
daemon=300

Commenting out by adding # in front of
mail=root       
mail-failure=root
if you do not want any messages. This is optional.

Uncomment the line by deleting the # sign at the begining of the line
#use=web, web=checkip.dyndns.org/, web-skip='IP Address' # found after IP Address
so that it looks like
use=web, web=checkip.dyndns.org/, web-skip='IP Address' # found after IP Address

Uncomment this line
#protocol=dyndns2
so that it looks like this
protocol=dyndns2

Uncomment and edit the server name
#server=members.dyndns.org            # default server
so that it looks as follows
server=updates.opendns.com            # default server               

Uncomment and insert your username and password here
#login=your-login                # default login
#password=test                    # default password
For example, if your username is alfred and your password is hitchcock, these lines will look as follows
login=alfred                # default login
password=hitchcock                    # default password

Create an empty line immediately after this line and type the network label of your opendns network. For example my network label is home, so I simply type, in a new line

home

Save changes in the editor and exit.

# Copying the init script:
**sudo cp sample-etc_rc.d_init.d_ddclient.lsb /etc/init.d/ddclient**

#Edit startup script. In the official documentation, this step is not mentioned. If you open the above script as follows
sudo vi /etc/init.d/ddclient
you will see this line
start_daemon $DDCLIENT_BIN -daemon 300
a command for the daemon to update every 300 seconds. If you change this value in the ddclient.conf, then there will be a conflict. My experience is that the time mentioned here is followed, and not what is in the ddclient.conf ! So if you changed the time when editing the ddclient.conf file (it's the first change listed above in that file), then make the same change here too. For example if you changed 300 to 900 in the ddclient.conf file, change the 300 to 900 here too.

## enable automatic startup when booting
**sudo update-rc.d ddclient defaults**

# start the first time by hand
**sudo /etc/init.d/ddclient start**

#Check for running process
**ps aux | grep ddclient**
and press ENTER

You will see something like this
root      2989  0.0  0.4   6372  4288 ?        S    23:14   0:00 ddclient - sleeping for 420 seconds
neville   5828  0.0  0.0   3340   788 pts/0    S+   23:22   0:00 grep ddclient

and check if your ip is getting updated in the dashboard of your opendns account. The first and subsequent updates take place after the time delay you specified above. For example if you left it at default (300), then it is only 300 seconds after you boot up that your IP gets updated. So don't be surprised if your IP is not updated "immediately", as soon as the boot process is complete :)

---

### Post by LaneLester on 2010-03-23
I can't believe that no one has thanked you for the valuable post. I also can't believe how useless the OpenDNS site's explanation is. I also can't believe how incomplete is the help that comes with ddclient.

You've made a real contribution to our community.

Lane

---

### Post by nucleuskore on 2010-03-24
You're welcome !
It's had 885 views, guess people just forget to come back :)

---

### Post by LaneLester on 2010-03-24
You said, "...check if your ip is getting updated in the dashboard of your opendns account."

I clicked the various tabs at the site, but I don't find where that is displayed.

I have a DSL line, so I guess the IP doesn't change unless the current one gets released somehow.

Lane

---

### Post by nucleuskore on 2010-03-25
In the settings tab. If you do not see your network listed under Manage your networks then you have to add your network using the boxes in the same page

---

### Post by Gadaph on 2010-07-28
Thank you so much for putting this together.

I put an evening aside to configure OpenDNS, but then found this, and had it all done in an hour!

As has been previously mentioned, I really appreciate your contribution to our community.

Gadaph

---

### Post by pizzaman1 on 2010-09-01
thanks for a great tutorial i just have managed to get it to work mostly, except a few issues. i am using namecheap.com

the @ does not resubmit the new ip when it is same as the old one which is a good thing.

but www does not update, it say that the www was tried before and  although not successful but still have to wait for 5 minutes. this keeps  on happening no matter how long i wait.

* updates all the time no matter if it is a new ip or an oldone.

also why aren't you using
**sample-etc_rc.d_init.d_ddclient.ubuntu**
in
**sudo cp sample-etc_rc.d_init.d_ddclient.lsb /etc/init.d/ddclient**

---

### Post by nucleuskore on 2010-09-01
If you see the date of the tutorial, it is September 12th 2009. September 30th 2009 was my last working day in that institution. I am a professional microbiologist and I haven't really got a chance to get ANYWHERE near the systems in the University I work for now. I am sorry I'm cannot answer your question.

---

### Post by pizzaman1 on 2010-09-02
thank you for the reply and good luck in your new job. i got it almost working

---

### Post by nucleuskore on 2010-09-02
Thank you, and whatever you do successful or not, please leave your feedback. It will be very helpful for other users !

---

### Post by pizzaman1 on 2010-09-02
i used this and now it is working great
[http://ubuntuforums.org/showthread.php?t=1543379&highlight=ddclient](http://ubuntuforums.org/showthread.php?t=1543379&highlight=ddclient)

---

### Post by Myfathersheart on 2011-01-11
> **nucleuskore said:**
> 
#Unpack the tarball
**tar xvf ddclient-**

and press TAB to auto complete. Press ENTER.




This isn't working for me when.  I am new to Ubuntu and codes so I may be typing it in wrong but what I am doing is simply typing this in a terminal:

tar xvf ddclient- 

then I hit tab and nothing happens then I hit enter and I get this:

tar: ddclient-: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


Any ideas?

---

### Post by nucleuskore on 2011-01-24
> **Myfathersheart said:**
> This isn't working for me when.  I am new to Ubuntu and codes so I may be typing it in wrong but what I am doing is simply typing this in a terminal:

tar xvf ddclient- 

then I hit tab and nothing happens then I hit enter and I get this:

tar: ddclient-: Cannot open: **No such file or directory**
tar: Error is not recoverable: exiting now


Any ideas?

Are you downloading it directly to your PC with the idea of installign it on your pc and not a remote machine? Which browser are you using?

---

### Post by warroomcbw on 2011-04-03
I thank you, but this is beyond my abilities.  I did the router set up, and now I have asked my church to use it which I think they will do.  I really can't beleive how bad the help is that comes with this.   thank you again.  you did your homework.

cbw

---

### Post by SupaRice on 2012-09-18
Bump for something that helped a lot!

---

### Post by nucleuskore on 2012-09-18
Can't believe that people are still referring this!

---

