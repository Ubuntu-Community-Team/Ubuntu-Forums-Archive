---
title: "HOWTO: Security with webcam and Twitter"
date: 2008-12-03
forum: Security
---

### Post by LinuxPS2 on 2008-12-03
[UPDATED 12-10-08] Should all work
So here is the updated script - we will see how well it works soon enough

First install everything you need
```
sudo apt-get install postfix mutt cheese streamer libsasl2-2 libsasl2-modules
```

Now configure postfix, after installing do
```
sudo dpkg-reconfigure postfix
```
select ok; internet site; server1.example.com; leave this one blank; server1.example.com, localhost; NO; 127.0.0.1/8; 0; +; ALL

Now from [http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/]("http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/") do the following (assuming you use Gmail)
> 
Now do ```
sudo nano /etc/postfix/main.cf
```
and add this to the end of the file
```
relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_use_tls = yes
```

now exit and save

next do 
```
sudo nano /etc/postfix/sasl_passwd
```
and put this in it
```
[smtp.gmail.com]:587    user.name@gmail.com:password
```
replace the username and password
then run this
```
sudo chmod 400 /etc/postfix/sasl_passwd
sudo postmap /etc/postfix/sasl_passwd
```


Now we are going to create the script
```
sudo nano /etc/init.d/securetwit
```
and populate it with
```

#!/bin/bash
# Script by L|nuxPS2 with help from
# http://ubuntuforums.org/archive/index.php/t-129304.html : http://ubuntuforums.org/archive/index.php/t-526176.html
# and leftyfb from #ubuntu on EFnet
### BEGIN INIT INFO
# Provides:          securetwit
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: A just-for fun security measure that uses twitter
# Description:       Securetwit sends the picture and external IP address of whomever turns on a computer with a webcam
### END INIT INFO

IP=$(wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//')

streamer -c /dev/video0 -b 32 -o /etc/securetwit/pic.jpeg

echo | mutt -a '/etc/securetwit/pic.jpeg' -s "Someone is on your Laptop from $IP " USERNAME@twitpic.com

mv /etc/securetwit/pic.jpeg /etc/securetwit/pic.jpeg.old

exit 0

```
save and close it. now add it to the startup
```
update-rc.d securetwit defaults 99 
```
and make it executable
```
chmod +x /etc/init.d/securetwit
```
and make a folder for it to use to save everything in
```
sudo mkdir /etc/securetwit
```

restart and the script should work - the only problem I can see is that it will just fail to ping the websites and then not run - I just need to find a way to make it keep trying and upon success stop... all while running in the background... hrm... it might do that now, i'll see

[ORIGINAL POST]
>  So i don't know if this has been done before or if it falls under security but if not i'm sure a mod will put it where it should be...

This is my first script so don't get all pissy about how i did something wrong - I know I most likely did, think constructive and point me to some stuff that could help

Anyways, I just wrote a quick script that should be of some use if you have a laptop with a built in webcam (or a pc with a well situated webcam)

This uses Twitter and Twitpic to send a picture of whoever is on your computer whenever the script is run - that way you get an update sent to your phone with who is using it.

First its good if you make a new twitter account just for this - that way you can follow it and get the update to your phone - make sure its not on the public timeline and you should be good

some preliminary stuff
```
sudo apt-get install cheese streamer mutt sendmail
```
cheese just to see if your webcam is working, streamer to capture the frame from the webcam and output the file mutt to send it to twitpic and sendmail so you can actually use mutt...

right off the bat i have no eartly idea how the hell postfix manages to work but here is the guide I followed - sorry I am of no help in that department (and I mean NONE :P )
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p5](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p5)

Once you have that done were on to making the script
first: in your home directory
```
mkdir '.securetwit'
cd ~/.securetwit/
nano securetwit.sh
```

Now for making the shell script
```
#!/bin/bash

streamer -c /dev/video0 -b 32 -o ~/.securetwit/pic.jpeg

wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//' | mutt -a '/home/**[COLOR="RoyalBlue"]USER[/COLOR]**/.securetwit/pic.jpeg' -s "" '**[COLOR="RoyalBlue"]USER.NUMBER@twitpic.com[/COLOR]**'

mv ~/.securetwit/pic.jpeg ~/.securetwit/pic.jpeg.old

exit 0
```

Make sure to replace the bold and blue text with your username (I had trouble getting mutt to read the attachment from '~/.securetwit/pic.jpeg') and the link that twitpic will give you to send pictures to - also make sure your pics arent sent to the public timeline within twitpic

now just 
```
chmod +x securetwit.sh
```

Now add it to the startup programs or whenever you log in make it run automatically
Currently it outputs the external IP in the body of the email which is useless so if anyone knows how to make mutt let me put it as the subject please let me know... 

Obviously you could just make it email the picture to you but i'm sure there are plenty of better programs and whatnot that could do this - i just thought it would be fun for my first script to integrate twitter into things that way it can all be done via cell phone

None the less, Hope you enjoy it

-LinuxPS2

---

### Post by LinuxPS2 on 2008-12-04
Hey everyone... well I finally figured out how to make it have the IP adress in the subject... now it will send an update to twitter with the IP address of the computer as well as a picture of who is on it... this might be good for security, iunno... I just thought it was fun... hope this works for you...
Remember to replace the BOLD and BLUE text with things like your username and twitpic email (it's under settings on your twitpic site)
An props to these guys ([http://ubuntuforums.org/archive/index.php/t-526176.html](http://ubuntuforums.org/archive/index.php/t-526176.html)) for the external IP bit

```
#!/bin/bash

rm /home/[COLOR="Blue"]**USER**[/COLOR]/.securetwit/c*
rm /home/**[COLOR="Blue"]USER[/COLOR]**/.securetwit/ip

wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//' >> ~/.securetwit/ip

wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//' >> ~/.securetwit/ip.log

echo "#!/bin/bash" >> /home/**[COLOR="Blue"]USER[/COLOR]**/.securetwit/combine

echo -n "streamer -c /dev/video0 -b 32 -o ~/.securetwit/pic.jpeg

echo | mutt -a '/home/**[COLOR="Blue"]USER[/COLOR]**/.securetwit/pic.jpeg' -s 'Someone is on your Laptop from " >> ~/.securetwit/combine

cat /home/**[COLOR="Blue"]USER[/COLOR]**/.securetwit/ip >> /home/**[COLOR="Blue"]USER[/COLOR]**/.securetwit/combine

echo "' **[COLOR="Blue"]TWITTERUSERNAME.NUMBER[/COLOR]**@twitpic.com

mv ~/.securetwit/pic.jpeg ~/.securetwit/pic.jpeg.old


exit" >> /home/**[COLOR="Blue"]USER[/COLOR]**/.securetwit/combine

chmod +x /home/**[COLOR="Blue"]USER[/COLOR]**/.securetwit/combine &&

exec /home/[COLOR="Blue"]**USER**[/COLOR]/.securetwit/combine && rm /home/**[COLOR="Blue"]USER[/COLOR]**/.securetwit/combine

exit 0
```

I know i could just use '~' but I'm lazy (or rather I like to type our /home/USER) but I will edit this and clean it up over time.

Hope this works for all of you...

There is a screenshot attached.. sorry about the weird angle, I'm just chillin in my dorm and its kinda late...

---

### Post by nashrafeeg on 2008-12-04
hi i was wondering if any one know how to send image  via MMS using a attached phone rather than using twitter

---

### Post by LinuxPS2 on 2008-12-04
you don't have to have an attached phone... its easy... in the script where it says [email]TWITTERUSERNAME.NUMBER@twitpic.com[/email]... replace that with your cell phone email...

for example with 
alltell its <yournumber>@message.alltel.com
Verizon its <yournumber>@vtext.com

not sure what it is with other providers

easy way to check would be to text something to your email address and it will show it... good luck!... 

ps. I just tested it and it works for me on Verizon

---

### Post by nashrafeeg on 2008-12-04
i just tested it out with the operator i am using (maxis in malaysia) and it does not seem to work apparently they cancelled the service long time ago as they cant make money off it :(

---

### Post by ndefontenay on 2008-12-04
This is really simple and cool.

completely paranoid! but cool^^

---

### Post by LinuxPS2 on 2008-12-04
@nashrafeeg
Well there a number of MMS servers and stanalone boxes but I don't know how one would go about setting it up - just from googling it one of the 'popular' boxes is called foxbox and will read from a standard SIM card ([http://www.smsfoxbox.it/the_news/latest_news/mms_foxbox_unleashed!.html](http://www.smsfoxbox.it/the_news/latest_news/mms_foxbox_unleashed!.html)) but its damn pricey... 

Other than that I'm not really sure if a phone could be tethered and used... *off to google I go!!!* - I'll update this post if I can find a way

oh and here is a list of the Carriers that do support it for everyone else wondering:
US Based Carriers:
[http://basicstate.com/htm/page.htm](http://basicstate.com/htm/page.htm)
seems to have most carriers (atleast US ones and alot of EU ones)

---

### Post by LinuxPS2 on 2008-12-07
anyone know of a way to automatically connect to the nearest unprotected or previously configured wireless network so that I could put it at the top of the script that way if someone were to run it at startup there would be an IP to grab and also a way to disconnect so that I could break the connection at the end of the script?... just wondering, I want it to work correctly ALL the time... and I'm gonna clean up the script a bit after I find out how to do the previous thing. Thanks!
-LinuxPS2 ):P

---

### Post by LinuxPS2 on 2008-12-10
Checkout the updated script at the top :)
Enjoy
-L|nuxPS2

---

