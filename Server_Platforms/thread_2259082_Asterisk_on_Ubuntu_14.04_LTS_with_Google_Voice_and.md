---
title: "Asterisk on Ubuntu 14.04 LTS with Google Voice and MySQL Realtime"
date: 2015-01-01
forum: Server Platforms
---

### Post by Ryaz_Khan on 2015-01-01
First of all allow me to say that I don't issue any sort assurance that following will work for you. It did work for me and and I tested it few time and found it to be working every time. So now I am just sharing it the community, please let me know if you have any question(s) and I would be more than happy to answer them to best of knowledge. 
Content
1. Basice Setup
2. Google Voice Setup
3. MySQL Realtime Setup


Be root rather than typing password on every single command or getting sudo error 
> sudo bash
Install the packages we need 
> sudo apt-get install apache2 libapache2-mod-php5 phpmyadmin mysql-server asterisk asterisk-doc asterisk-mysql -y
Configure mcrypt for php, otherwise you probably will get warning/error in phpmyadmin portal 
> php5enmod mcrypt; service apache2 restart
We will configure asterisk step by step and will test it on every stept to check our configuration. So lets start 
[SIZE=6]Basic Setup
[/SIZE]Backup the whole directory before we do any damage 
> cp -fr /etc/asterisk/ ~
Lets start with editing/updating rtp.conf. We need this regardless, you can just simply paste these values in terminal but DO NOT FORGET TO CHANGE THE VARIABLES ACCORDINLY 
> 
cat << EOT > /etc/asterisk/rtp.conf
[general]
icesupport=yes
rtpstart=10000
rtpend=20000
EOT

Nex, update the sip.conf file, make sure to adjust ip, port and mask for your enviornment aftward by edit /etc/asteris/sip.conf configuration file. 
> 
cat << EOT > /etc/freeradius/sip.conf
[general]
localnet=10.10.10.0/255.255.255.0
nat=force_rport,comedia
rtcachefriends=yes  
udpbindaddr=10.10.10.30:9065 
tcpenable=no
;tcpbindaddr=0.0.0.0
allowguest=yes                  
match_auth_username=yes         
allowoverlap=yes                
g726nonstandard=yes           
srvlookup=yes
pedantic=yes
useragent=Asterisk PBX
dtmfmode=rfc2833
;videosupport=yes
alwaysauthreject=yes
engine=asterisk 
disallow=all
allow=ilbc
;allow=g729
allow=gsm
;allow=g723
allow=ulaw
qualifyfreq=30
qualifygap=100
qualifypeers=1
  
[demo.10]
type=peer
secret=demo10
host=dynamic
context=internal

[demo.11]
type=peer
secret=demo11
host=dynamic
context=internal
EOT

Next, configure extensions.conf file 
> 
cat << EOT > /etc/asterisk/extensions.conf
[internal]
exten => 10,1,Dial(SIP/demo.10,,r)
exten => 11,1,Dial(SIP/demo.11,,r)
Hangup()
EOT

Restart service 
> service asterisk restart
At this poing you should be able to register two user (demo.10,demo11) and both should be able to call each other by dialing their extensions (10, 11) 

[SIZE=6]Add Google Voice Support[/SIZE]
Set google voice to make and receive calls. Lets starting configuring motif so edit motif.conf 
> 
cat << EOT > /etc/asterisk/motif.conf
[google]
context=incoming-motif
disallow=all
allow=ulaw
connection=google
EOT

Next file we need to configure is xmpp.conf 
> 
cat << EOT > /etc/asterisk/xmpp.conf
[general]
[google]
type=client
serverhost=talk.google.com
username=xxx@gmail.com
secret=xxx
priority=127
port=5222
usetls=yes
usesasl=yes
status=available
statusmessage="I am available"
timeout=5
EOT

Update extensions.conf to configure google support for inbound and outbound calls 
Backup the original configuration file 
> mv /etc/asterisk/extensions.conf /etc/asterisk/extensions.conf.orig; nano /etc/asterisk/extensions.conf
Now paste the following in extensions.conf, save and exit out of it, dont forget to adjust the variables 
> 
[general]
[incoming-motif]
exten => s,1,Answer()
same => n,Wait(1)
same => n,SendDTMF(1)
same => n,Set(cid=${CALLERID(name)})
same => n,Set(cid=${CUT(cid,@,1)})
same => n,Set(CALLERID(all)=${cid})
same => n,Dial(SIP/demo.10,20,D(:1))
  
[internal]
exten => 10,1,Dial(SIP/demo.10,,r)
exten => 11,1,Dial(SIP/demo.11,,r)
exten => _1NXXNXXXXXX,1,Dial(Motif/google/${EXTEN}@voice.google.com,,r)
exten => _NXXNXXXXXX,1,Dial(Motif/google/1${EXTEN}@voice.google.com,,r)
exten => _NXXXXXX,1,Dial(Motif/google/1xxx${EXTEN}@voice.google.com,,r)
Hangup()

Restart the asterisk service 
> service asterisk restart
At this point you should be able to call your gooogle voice number and demo.10 extension should ring. Both extensions (demo.10 and demo.11) should be call outside as well. replace xxx before ${EXTEN} with your area code. 

[SIZE=6]Add MySQL Support[/SIZE]
Lets start with configuring call detail records (cdr)cdr_mysql.conf for realtime 
> 
cat << EOT > /etc/asterisk/cdr_mysql.conf
[global]
hostname = localhost
dbname = asterisk
table = astCDR
password = asterisk
user = asterisk
port = 3306
sock = /var/run/mysqld/mysqld.sock
EOT

Now lets configure extconfig.conf for realtime 
> cat << EOT > /etc/asterisk/extconfig.conf
[settings]
sippeers => mysql,asterisk,astAccounts
extensions => mysql,asterisk,astExtensions
voicemail => mysql,asterisk,astVoicemails
queues => mysql,asterisk,astQueue
queue_members => mysql,asterisk,astQueueMembers
meetme => mysql,asterisk,astMeetme
EOT

Now finally configure res_config_mysql.conf to make MySQL realtime connection 
> 
cat << EOT > /etc/asterisk/res_config_mysql.conf
[asterisk]
dbhost = localhost
dbname = asterisk
dbuser = asterisk
dbpass = asterisk
dbport = 3306
dbsock=/var/run/mysqld/mysqld.sock
dbcharset = latin1
requirements=warn ; or createclose or createchar
EOT

Update sip.conf to exclude user information 
> mv /etc/asterisk/sip.conf /etc/asterisk/sip.conf.orig
cat << EOT > /etc/asterisk/sip.conf
[general]
localnet=10.10.10.0/255.255.255.0
nat=force_rport,comedia
rtcachefriends=yes  
udpbindaddr=10.10.10.30:9065 
tcpenable=no
;tcpbindaddr=0.0.0.0
allowguest=yes                  
match_auth_username=yes         
allowoverlap=yes                
g726nonstandard=yes           
srvlookup=yes
pedantic=yes
useragent=Asterisk PBX
dtmfmode=rfc2833
;videosupport=yes
alwaysauthreject=yes
engine=asterisk 
disallow=all
allow=ilbc
;allow=g729
allow=gsm
;allow=g723
allow=ulaw
qualifyfreq=30
qualifygap=100
qualifypeers=1
  
;[demo.10]
;type=peer
;secret=demo10
;host=dynamic
;context=internal


;[demo.11]
;type=peer
;secret=demo11
;host=dynamic
;context=internal
EOT

Now update extensions.conf for realtime settings 
> mv /etc/asterisk/extensions.conf /etc/asterisk/extensions.conf.orig; nano /etc/asterisk/extensions.conf
Paste the following in it, basically tell asterisk to use mysql realtime database (asterisk) to read all configuration. 
> 
[general]
[incoming-motif]
;exten => s,1,Answer()
;same => n,Wait(1)
;same => n,SendDTMF(1)
;same => n,Set(cid=${CALLERID(name)})
;same => n,Set(cid=${CUT(cid,@,1)})
;same => n,Set(CALLERID(all)=${cid})
;same => n,Dial(SIP/demo.10,20,D(:1))
switch => Realtime/@
  
[internal]
;exten => 10,1,Dial(SIP/demo.10,,r)
;exten => 11,1,Dial(SIP/demo.11,,r)
;exten => _1NXXNXXXXXX,1,Dial(Motif/google/${EXTEN}@voice.google.com,,r)
;exten => _NXXNXXXXXX,1,Dial(Motif/google/1${EXTEN}@voice.google.com,,r)
;exten => _NXXXXXX,1,Dial(Motif/google/1xxx${EXTEN}@voice.google.com,,r)
;Hangup()
switch => Realtime/@

Now server is pretty much configured but we still need to create database.
I have the whole mysql script to add database and setup proper permission so download it first 
> wget [http://ryaz.homeip.net/dcs/conf/ast11.sql](http://ryaz.homeip.net/dcs/conf/ast11.sql)
Now login to mysql cli 
> mysql -u root -p
Create the database and setup permission 
> source ast11.sql; exit;
Finally restart the asterisk 
> service asterisk restart
Connect to asterisk console and check the realtime connection 
> asterisk -rvvv
Run the following command to see realtime status 
> realtime mysql status
Congratulation ! You have just configured asterisk for realtime and it is linked with your google account so enjoy making free calls forever.

This tutorial is also available on [http://ryaz.homeip.net/?p=42]("http://ryaz.homeip.net/?node=2&sub=37") and [http://ryazkhan.blogspot.com/2014/12/asterisk-on-ubuntu-1404-lts-with-google.html](http://ryazkhan.blogspot.com/2014/12/asterisk-on-ubuntu-1404-lts-with-google.html)

---

