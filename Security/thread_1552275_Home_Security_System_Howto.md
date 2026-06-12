---
title: "Home Security System Howto:"
date: 2010-08-13
forum: Security
---

### Post by jeff.sadowski on 2010-08-13
I decided to make my own home brew security system and thought it would be nice to share my code.

I bought one of these
[http://www.desktopaviator.com/Products/Model_2040/index.htm](http://www.desktopaviator.com/Products/Model_2040/index.htm)
It is designed to add buttons to flight simulators but it worked perfect for my alarm system. It was $33

I wrote a small program to use it as follows

alarm.c

```

#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/stat.h>
#include <fcntl.h>

int main(int argc,char** argv)
{
 int fd,buttons;
 static char buttons_int[13];

 if(argc!=2)
 {
  fprintf(stderr,"Usage: alarm <script or program to run that reads the environment variable BUTTONS_INT>\n");
  exit(1);
 }

 if(fork())
 {/*Make a deamon*/
  exit(0);
 }

 while(1)
 {
  fd=open("/dev/alarm",O_RDONLY);
  read(fd,&buttons,sizeof(int));
  close(fd);
  snprintf(buttons_int,13,"%i",buttons);
  setenv("BUTTONS_INT",buttons_int,1);
  system(argv[1]);
  usleep(10000);
 }
 return 0;
}

```

compile it with
gcc -o alarm alarm.c

second_watch.c

```

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>

int main(int argc,char** argv)
{
 if(argc!=2)
 {
  fprintf(stderr,"Usage: second_watch <script to run every second>\n");
  exit(1);
 }

 if(fork())
 {/*Make a deamon*/
  exit(0);
 }

 while(1)
 {
  system(argv[1]);
  sleep(1);
 }
 return 0;
}

```

to compile
gcc -o second_watch second_watch.c

sudo cp alarm /usr/sbin/alarm
sudp cp second_watch /usr/bin/

install mysql to make using it easy
sudo apt-get install mysql-server mysql-client

create a script to use with it

/root/alarm_script.sh
```

#!/bin/bash
. /etc/alarm/mysql_root_info.sh
. /etc/alarm/mysql_info.sh
. /etc/alarm/alarm_definitions.sh
. /etc/alarm/functions.sh
PADDING="000000000"

if [ "${BUTTONS_INT}" = "" ];then
BUTTONS_INT=`get_default`
fi
SINCEEPOCH=`date "+%s"`
NANOSECOND=`date "+%N"`

post(){
echo -e "insert into alarm (timestamp,nanosecond,state) values (${SINCEEPOCH},${NANOSECOND},${BUTTONS_INT});" | mysql "${database}" -u "${rootusername}" --password="${rootpassword}"
sleep 2;
activity=`echo "select timestamp,nanosecond,state from alarm order by timestamp desc,nanosecond desc limit 1;"|mysql ${database} -u "${username}" --password="${password}"|grep -v timestamp|awk '{print $1 "." $2 "-" $3}'`
TS=`echo ${activity}|cut -d. -f1`
NS=`echo ${activity}|cut -d. -f2|cut -d- -f1`
ST=`echo ${activity}|cut -d- -f2`
NS_SIZE=`echo -e ${NS}|wc -c`
let PADDING_NEEDED=10-${NS_SIZE}
if [ ${PADDING_NEEDED} -gt 0 ];then
NS=`echo ${PADDING} | cut -c ${PADDING_NEEDED}``echo -e "${NS}"`
activity=${TS}.${NS}-${ST}
fi

old_state=`echo "select timestamp,nanosecond,state from state order by timestamp desc,nanosecond desc limit 1;"|mysql ${database} -u "${username}" --password="${password}"|grep -v timestamp|awk '{print $3}'`

if [ "${SINCEEPOCH}.${NANOSECOND}-${BUTTONS_INT}" = "${activity}" ] && [ "${BUTTONS_INT}" != "${old_state}" ];then
 echo -e "insert into state (timestamp,nanosecond,state) values (${SINCEEPOCH},${NANOSECOND},${BUTTONS_INT});" | mysql "${database}" -u "${rootusername}" --password="${rootpassword}"
else
 if [ "${BUTTONS_INT}" != "${old_state}" ];then
  echo "${SINCEEPOCH}.${NANOSECOND}-${BUTTONS_INT}" != "${activity}" > /tmp/chatter.txt
 else
  echo state has not changed > /tmp/chatter.txt
 fi
fi
}
post &

```

create a script to start it via crontab

/root/checkalarm.sh

```

alarmpid=`ps h -C alarm`
if [ "$alarmpid" = "" ];then
/root/alarm /root/alarm_script.sh
fi

```

sudo crontab -e

```

* * * * * /root/checkalarm.sh

```

create scripts to use it from a regular user

second_watch_alarm.sh

```

#!/bin/bash
. /etc/alarm/alarm_definitions.sh
. /etc/alarm/functions.sh
. /etc/alarm/mysql_info.sh
lastseenfile=${HOME}/.alarm/lastseen.txt

cd ${HOME}/.trusted
recipients=`ls -1 *@* 2>/dev/null`
email_recipients=`echo -e "${recipients}"|grep -v "[0-9]\{9\}@.*"`
phone_recipients=`echo -e "${recipients}"|grep "[0-9]\{9\}@.*"`

lump_10()
{
 if [ ! -f ${lastseenfile} ];then
  mkdir -p ${HOME}/.alarm
  echo 0.0 > ${lastseenfile}
 fi

 lastseen=`cat ${lastseenfile}`
 TS="`echo -e "${lastseen}"|cut -d. -f1`"
 NS="`echo -e "${lastseen}"|cut -d. -f2`"

 activity=`echo "select timestamp,nanosecond,state from state where (timestamp > ${TS}) or (timestamp = ${TS} and nanosecond 
> $NS) order by timestamp desc,nanosecond desc;"|mysql ${database} -u "${username}" --password="${password}"|grep -v timestam
p|awk '{print $1 "." $2 "-" $3}'`

 if [ "`echo -e "${activity}"|wc -c`" = "1" ];then
  return
 fi
 sleep 10;

 if [ ! -f ${lastseenfile} ];then
  mkdir -p ${HOME}/.alarm
  echo 0.0 > ${lastseenfile}
 fi

 lastseen=`cat ${lastseenfile}`
 TS="`echo -e "${lastseen}"|cut -d. -f1`"
 NS="`echo -e "${lastseen}"|cut -d. -f2`"

 activity=`echo "select timestamp,nanosecond,state from state where (timestamp > ${TS}) or (timestamp = ${TS} and nanosecond > $NS) order by timestamp desc,nanosecond desc;"|mysql ${database} -u "${username}" --password="${password}"|grep -v timestamp|awk '{print $1 "." $2 "-" $3}'`

 lastseennow=`echo -e "$activity" | head -n 1|cut -d- -f1`
 if [ "${lastseennow}" != "" ];then
  echo ${lastseennow} > ${lastseenfile}
 fi

 for item in `echo -e "${activity}"`; do
  TS="`echo ${item}|cut -d. -f1`"
  ST="`echo ${item}|cut -d- -f2`"
  TSH=`date -d @${TS} "+%H:%M:%S"`
  echo "${TSH} `alarm_status ${ST}`"
 done
}

watcher()
{
 sleep 1;
 data="`lump_10`"
 if [ "$data" != "" ]; then
  for recipiant in ${email_recipients}; do
   if [ -f ${HOME}/.armed/${recipiant} ];then
    /bin/echo -e "$data" | sudo /usr/sbin/scripts/sendEmail \
          -t "${recipiant}" \
          -u "alarm status `date "+%F"`" \
          1> /dev/null 2>/dev/null
   fi
  done
  for recipiant in ${phone_recipients}; do
   if [ -f ${HOME}/.armed/${recipiant} ];then
    /bin/echo -e "$data" | sudo /usr/sbin/scripts/sendEmail \
          -t "${recipiant}" \
          1> /dev/null 2>/dev/null
   fi
  done
 fi
}

watcher

```

watcher.sh
```

#!/bin/bash
watch(){
running=`ps h -f -C second_watch|grep ^\`whoami\`\ `
if [ "${running}" = "" ]; then
 second_watch ${HOME}/second_watch_alarm.sh
fi
}

watch 2>/dev/null >/dev/null

```


make sure it gets started using crontab
crontab -e
```

* * * * * ${HOME}/watcher.sh

```

create the common files

/etc/alarm/alarm_definitions.sh
```

# the item names are the name you want it to send you
# the stat names are the default state of each
# for normally open switches(most alarm reed switches)
# the default state is 0
# for normally closed switches ( I found a couple of these for my windows that I wired in parallel) 
# the default state is 1 
# also disconnected items default states are 0
STATION_ITEM[1]="Front Door";
STATION_STAT[1]="0";
STATION_ITEM[2]="Bedroom Window";
STATION_STAT[2]="0";
STATION_ITEM[3]="Living Room Window";
STATION_STAT[3]="1";
STATION_ITEM[4]="Station 4";
STATION_STAT[4]="1";
STATION_ITEM[5]="Station 5";
STATION_STAT[5]="1";
STATION_ITEM[6]="Station 6";
STATION_STAT[6]="1";
STATION_ITEM[7]="Station 7";
STATION_STAT[7]="1";
STATION_ITEM[8]="Station 8";
STATION_STAT[8]="1";
STATION_ITEM[9]="Station 9";
STATION_STAT[9]="1";
STATION_ITEM[10]="Station 10";
STATION_STAT[10]="1";
STATION_ITEM[11]="Station 11";
STATION_STAT[11]="1";
STATION_ITEM[12]="Station 12";
STATION_STAT[12]="1";
STATION_ITEM[13]="Station 13";
STATION_STAT[13]="1";
STATION_ITEM[14]="Station 14";
STATION_STAT[14]="1";
STATION_ITEM[15]="Station 15";
STATION_STAT[15]="1";
STATION_ITEM[16]="Station 16";
STATION_STAT[16]="1";
STATION_ITEM[17]="Station 17";
STATION_STAT[17]="1";
STATION_ITEM[18]="Station 18";
STATION_STAT[18]="1";
STATION_ITEM[19]="Station 19";
STATION_STAT[19]="1";
STATION_ITEM[20]="Station 20";
STATION_STAT[20]="1";

```
chmod 0755 /etc/alarm/alarm_definitions.sh

/etc/alarm/mysql_info.sh
```

username=alarmviewer
password=alarmviewerpassword
database=alarm

```
chmod 0755 /etc/alarm/mysql_info.sh

/etc/alarm/mysql_root_info.sh
```

rootusername=root
rootpassword=password4mysql_root_user

```
chmod 0700 /etc/alarm/mysql_root_info.sh


/etc/alarm/functions.sh
```

get_default(){
 full=00000000000000000000000000000000
 bin=""
 for counter in 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20; do
  if [ ${STATION_STAT[${counter}]} = 0 ];then
   bin="1${bin}"
  else
   bin="0${bin}"
  fi
 done
 let len=33-`echo $bin | wc -c`
 echo 10o2i${pad}${bin}p | dc
}

int2bin()
{
 full=00000000000000000000000000000000
 bin=`echo 2o10i${1}p | dc 2>/dev/null`
 let len=33-`echo $bin | wc -c`
 pad=`echo ${full}|cut -c 1-${len}`
 echo ${pad}${bin}
}

alarm_status()
{
OPENED=""
BUTTONS=`int2bin $1`
for counter in 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20; do
 let otherend=33-counter;
 BUTTON=`echo $BUTTONS|cut -c $otherend`;
 if [ "$BUTTON" = "${STATION_STAT[$counter]}" ];then
  OPENED="${OPENED}${STATION_ITEM[$counter]},";
 fi
done

if [ "${OPENED}" = "" ];then
 echo "all closed"
else
 echo -e "${OPENED}" | sed s/",$"//
fi
}

```
chmod 0755 /etc/alarm/functions.sh

create the udev using this script
```

serial=`sudo lsusb -d 6017:3522 -v|grep iSerial|awk '{print $3}'`
echo KERNEL==\"hidraw\*\", ATTRS{manufacturer}==\"Desktop Aviator\", ATTRS{product}==\"Digital Switch 2040\" , ATTRS{serial}==\"$serial\" , SYMLINK+=\"alarm\" > 50-alarm.rules
sudo cp 50-alarm.rules /etc/udev/rules.d/
rm 50-alarm.rules
sudo service udev restart

```

create the database using this script
```

. /etc/alarm/mysql_info.sh
. /etc/alarm/mysql_root_info.sh
echo "create database ${database};" | mysql -u ${rootusername} --password="${rootpassword}"
echo "create table alarm (timestamp bigint,nanosecond int,state int);" |mysql ${database} -u ${rootusername} --password="${rootpassword}"
echo "create table state (timestamp bigint,nanosecond int,state int);" |mysql ${database} -u ${rootusername} --password="${rootpassword}"
echo "create user '${username}'@'localhost' IDENTIFIED BY '${password}';"|mysql -u ${rootusername} --password="${rootpassword}"
echo "grant select on ${database}.* to '${username}'@'localhost' identified by '${password}';"|mysql -u ${rootusername} --password="${rootpassword}"

```

create sendEmail script
/usr/sbin/scripts/sendEmail
```

#!/bin/bash
username="gmail_account_for_computer"
password="gmail_password"

sendEmail -f "${username}@gmail.com" \
          -s smtp.gmail.com:587 \
          -o tls=yes \
          -xu "${username}" \
          -xp "${password}" \
          $*

```
chmod 0700 /usr/sbin/scripts

add users that can send email to sudoers

echo ALL  ALL=NOPASSWD:/usr/sbin/scripts/sendEmail >> /etc/sudoers

================================================================

I saw an arduino for $25  here [http://shop.amcnano.com/Arduino-Duemilanove-SKU2001.htm](http://shop.amcnano.com/Arduino-Duemilanove-SKU2001.htm)
there are not as many inputs but plenty for most home security systems. When I get a hold of one I will try replacing my alarm system. There shouldn't be many modifications needed to implement the arduino

---

### Post by rookcifer on 2010-08-13
LOL, dude, that is some GEEK stuff right there. :P  I think we should give you some sort of award for geek project of the year or something. ;)

---

### Post by jeff.sadowski on 2010-08-14
> **rookcifer said:**
> LOL, dude, that is some GEEK stuff right there. :P  I think we should give you some sort of award for geek project of the year or something. ;)

You have to wait I'm getting a relay control board that I will use to control my garage door and maybe a sprinkler system. :-)

I also have a usb thermometer that I may use with my relay controller to act as a thermostat.

I also setup my computer to read email from my addresses and can send it commands. I will post that code latter.

---

### Post by CharlesA on 2010-08-14
That sounds like an interesting project. :)

---

### Post by sladekal on 2011-03-12
This looks exactly like what i have been looking for. Just a few questions. What about power requirrments for a switch say 25 feet away, or some kind of 10 to 1 or 20 to 1 wireless sensors?

---

### Post by BkkBonanza on 2011-03-12
What I don't understand is: if you have written a C program to do part of this then why not just make the C program do the whole thing? It appears you monitor switches and log them to mysql, and it seems you have a crontab to start scripts that then monitor another script, or something.

Why not just have a C program that starts and runs as daemon that monitors the switches and logs to mysql. You can connect and write to mysql from within C very easily using the mysql client library. That would be simpler. 

You start the daemon during boot by adding an init conf file and it will be monitored by init anyway (so that if it gets killed it will be restarted automatically). No need for watcher scripts and crontabs. 

Anyway, just saying. As it looks interesting but a rather complicated approach.

(note, is your sendEmail script recursive? it appears to call itself and seems like an error. shouldn't it be calling sendmail?)

---

### Post by jeff.sadowski on 2011-03-12
> **BkkBonanza said:**
> What I don't understand is: if you have written a C program to do part of this then why not just make the C program do the whole thing? It appears you monitor switches and log them to mysql,

I believe in the old unix way to use programs that already exist for the majority of the work. I could have had the c program work with mysql and all but I think it would have been more complicated and database specific.
I like the database approach but with my simple program its easy to modify it to do it any number of ways.
> **BkkBonanza said:**
> 
and it seems you have a crontab to start scripts that then monitor another script, or something.
Because I wasn't sure how reliable it was I wanted it to restart itself if it stopped running also it helps restart it if I unplug it and replug it back in.
> **BkkBonanza said:**
> 
Why not just have a C program that starts and runs as daemon that monitors the switches and logs to mysql. You can connect and write to mysql from within C very easily using the mysql client library. That would be simpler. 

answered above.
> **BkkBonanza said:**
> 
You start the daemon during boot by adding an init conf file and it will be monitored by init anyway (so that if it gets killed it will be restarted automatically). No need for watcher scripts and crontabs. 

I may look into moving it out of cron as it creates a lot of log entries in syslog however startup script may not be the best option as I may unplug it or it may get killed (looking less likely as it has been pretty reliable)
> **BkkBonanza said:**
> 
Anyway, just saying. As it looks interesting but a rather complicated approach.

Maybe I could make it a little easier but I love how I can run applications from email and I use that scripting to arm the alarm.
Its a hodge podge of exiting scripts that I use for all sorts of things.

> **BkkBonanza said:**
> 
(note, is your sendEmail script recursive? it appears to call itself and seems like an error. shouldn't it be calling sendmail?)
Yes it is recursive. I was running into trouble with it only reading one email per minute as I sent it email and now it works good. It should stop when there is no email left. I'll walk through it and make sure its doing what I say but it hasn't slowed down the box yet and its been running for about 4 months now.

You don't really need a database method but before I did that I was running into all sorts of race conditions and I didn't feel like writing a lot of locks and unlocks. I didn't want to deal with it. It sort of creates a database in my email as I set my email address as always armed.

-------------------------------------

I also added a motion sensor and I'll see if I can explain how to hook it up. But I wouldn't recommend it for someone that isn't familiar with diodes. Pretty much you want to keep the high(+5V) from reaching the return pin of the switch and allow the ground to flow. I'm using a radio shack one that I picked up for about $10.

Also I have about 30 events per day notes for anyone interested in implementing this. Its too many for my phone(I don't have a cellphone plan that has unlimited text messages) so I only arm it from time to time. I try to remember to arm it when I leave and disarm it about when my wife gets home. I also may wish to add noise creators but not sure what I want to do with this it may be more helpful if its quite as the cops may be able to catch them. I also have my house wired with a cat5 out to a port facing the front and back porches that I want to figure out a good way to put a camera in those two locations. I tried usb to cat5 converters (which I use with my alarm and you can get for $15) but the usb cameras I tried using didn't work well over them. I'll try some cheaper usb1 cameras that should work better with the cheaper usb over cat5 converters there is also the option of getting $300 convertors to support hi-def usb cameras that I want to use.

---

### Post by jeff.sadowski on 2011-03-12
> **sladekal said:**
> This looks exactly like what i have been looking for. Just a few questions. What about power requirrments for a switch say 25 feet away, or some kind of 10 to 1 or 20 to 1 wireless sensors?

This may be why I have a few glitches from time to time but they could also be from the wind hitting the window enough to cause it to wiggle the switch. In any effect. It seems to work ok for me. For its price I though it was worth testing. It works pretty good for me. I have some of my switches more than 20 feet away. Alarm systems don't use something all that different. Its a detect for continuity. The computers they use are dumb in comparison I learned that they too have a jitter detect and wait a bit of time on a switch action. Oh and that is why I use two tables in my database. If someone has a better way I'd like to see it.

---

### Post by BkkBonanza on 2011-03-13
The problem with switch contacts is handled using what is called "debouncing" in embedded systems projects or electronics. You can usually handle it with by testing twice 10-15 millseconds apart and making sure the value is consistent. So a small delay and re-confirm the read should work.

I'm not sure what tech the board's chips are based on but typically cmos/ttl levels signals degrade after about 10 ft or so due to wire resistance causing signal loss/corruption. Again the debouncing should help but also there are driver chips that are better suited than others for long line signals. Sometimes a transistor on the input can be used to clean it up but that's a hassle when it's not built in. 

There are wifi cameras around that could send video to your network. They're a fair bit more costly than the cheap usb webcams though. I helped a friend set up a video monitoring system for his restaurant using some linux webcam grabber software and usb webcams. But usb again isn't very good at long distances and my experience with the extenders and cat5 converters was very inconsistent. They work far better for single frame grabs at intervals than video streams.

Another approach I thought of before but didn't follow through on - that would give awesome quality - is using a cheap digicam and an **Eye-Fi** SD memory card that sends the images via wifi to the computer. Neither are real cheap but they're not that costly either.

---

### Post by jeff.sadowski on 2011-03-13
> **BkkBonanza said:**
> 
There are wifi cameras around that could send video to your network.

Wifi and security are nearly mutually exclusive. You can lock it down by some degree but no matter what its going over the air. Also wifi cameras come in to the price range of me just wanting to go another route anyways.

---

### Post by politick on 2011-08-16
How did you get the board to show up as: /dev/alarm
When I connect it I get a /dev/hidraw0

Then I used the program below and I only get 2 readings and it BLOCKS...
Note: The game controller works fine under windows.

Martin Politick.
```

-----------------------------------------------------
Program:
-----------------------------------------------------
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
#include <stdint.h>
int main(int argc,char** argv)
{
int x,y;
uint32_t  button;
int fd=open("/dev/hidraw0",O_RDONLY);
while(1)
{
        read(fd,&button,sizeof(button));
        printf(" 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0\n");
        for(x=0;x<20;x++)
        {
                y=1<<x;
                if(y&button)
                        printf(" 1");
                else
                        printf(" 0");
        }
        printf("\n\n");
        sleep(1);
}
return 0;
}

-----------------------------------------------
lsusb
-----------------------------------------------

 idVendor           0x6017
  idProduct          0x3522
  bcdDevice            0.01
  iManufacturer           1 Desktop Aviator
  iProduct                2 Digital Switch 2040
  iSerial                 3 DTA00957
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.01
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      29
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0003  1x 3 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by jeff.sadowski on 2011-08-17
The /dev/alarm was created with the udev section I created a script to create specific for the serial of the one I have connected. Thus I can hook 2 up afterwards and only one would show as the /dev/alarm

---

### Post by jeff.sadowski on 2011-08-17
try putting the open and close inside the loop.

---

### Post by handy on 2011-08-17
If you use an Arduino, you can either expand the number of outputs by adding one or more 74HC595:

[http://tronixstuff.wordpress.com/2010/04/30/getting-started-with-arduino-%E2%80%93-chapter-four/](http://tronixstuff.wordpress.com/2010/04/30/getting-started-with-arduino-%E2%80%93-chapter-four/)

There are a lot of great tutorials on that site. :)

Or by using the more expensive Arduino Mega 2560:

[http://australianrobotics.com.au/products/arduino-mega-2560](http://australianrobotics.com.au/products/arduino-mega-2560)

---

### Post by politick on 2011-08-17
Got my driver to work,
I had to use the /dev/input/eventX instead.

It looks like there is no debouncing on the inputs.
I guess I'll have to fix it by software.
Did you have that issue?  Multiple on/off before the switch value settles?
 

Here's the (not clean but working) code:

-------------------------------------------
```

#include <stdio.h>
#include <stdlib.h>
#include <stdint.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/ioctl.h>
#include <fcntl.h>
#include <unistd.h>
#include <linux/input.h>
#include <string.h>




#define INPUT_DEVICE "/dev/input/event"
//#define INPUT_DEVICE "/dev/hidraw0"  /* Don't read this one, the Input Event is already reading it*/

#define USB_DEVICE_NAME "Desktop Aviator Digital Switch 2040"

#define KEY_RELEASE 0
#define KEY_PRESS 1
#define KEY_KEEPING_PRESSED 2


int main(int argc,char** argv)
{
struct input_event    Event[64];
int                   i  =0;
int                   fd =0;


//// Find the Aviator device
for( i=0 ; i<128  ; i++)
{
   char  InputEventName[128];
   sprintf(InputEventName, "%s%d", INPUT_DEVICE, i);
   printf("Opening device %s\n", InputEventName);
   fd=open( InputEventName ,O_RDONLY);
   if (fd == -1)
   {
      printf("No Aviator device was found on your system\n");
      return -1;
   }

   char  String[128];
   int StringLength = ioctl( fd, EVIOCGNAME(sizeof(String)), String );
   if (StringLength == 0)
   {
      close( fd );
      printf("Unable to read the Device name\n");
      continue;
   }

   printf("The Device on %s is: %s\n", InputEventName, String);
   if (strcmp( String, USB_DEVICE_NAME) == 0)
      break;
   else
   {
      close( fd );
   }
}


printf("\n\nCongratulation!!  The device was found!\n");
printf("You should now start opening and closing switches to see something.\n");
printf("Enjoy! from Martin Politick.\n");

// Since we're not reading /dev/hidraw0, this is no longer required.
/*int Failure = ioctl( fd, EVIOCGRAB, 1);
if (Failure)
{
 printf("Unable to grab control of the DeskTopNavigator!\n");
 return 2;
}*/


while(1)
{
        //// Read one or more events
        size_t ByteCount = read( fd, &Event, sizeof(Event));

        //// Check that we've received something valid.
        if( ByteCount < (int) sizeof(struct input_event))
        {
           //// Note: This part of the code was never tested.
           printf("Didn't receive full data structure.");
           sleep(1);
           continue;
        }

        //// For each event, print it
        for ( i=0 ; i < (int) ( ByteCount / sizeof(struct input_event)); i++)
        {
            if (EV_KEY == Event[i].type)
            {
                    printf("type %d code %d value %d\n", Event[i].type, Event[i].code, Event[i].value);
            }
        }
}
return 0;
}

```

---

### Post by handy on 2011-08-17
Using the Processing IDE with the Arduino (& compatible) boards, you add a delay after the button press to handle that problem.

I guess it is as simple in C too.

---

### Post by jeff.sadowski on 2011-08-17
Yes I did have debounce issues. Hence my second database.
I'd also recommend a nanosleep or so in your loop otherwise you take all the resources with your code.

---

### Post by jeff.sadowski on 2011-08-17
The Arduino has the added benefit that you can use outputs from it to controls a siren.

---

### Post by politick on 2011-08-18
> I'd also recommend a nanosleep or so in your loop otherwise you take all the resources with your code.

The program does not consume CPU, the read(Event); is a blocking call.  It stays there until an event comes in through the generic input driver.  That's because I'm not talking directly to the USB device but to the HID Input device driver.

---

### Post by politick on 2011-08-18
> The Arduino has the added benefit that you can use outputs from it to controls a siren.

My situation is slightly different. 
I already have and old POS alarm system.

What I wanted is to be able to monitor it via a Web page and send email notifications if an alarm occurs.
I looked at Web enabled alarm panels, they are either very expensive or
don't give me the functionality I wanted. Most of them usually "sold" the web monitoring service, there's one that was free, but it was hosted by the manufacturer... I don't want the manufacturer to know the status of my home alarm system, even if the service is free.

So now I have 4 relays in parallel with the siren and 3 status (Ready, armed, Exit delay) in my alarm panel.  So if the alarm goes off, he bell sounds and my relay closes. 

BTW **I want to thank you for starting this project**
I've wanted to do it for a while but never got around doing it.
You have a good base on which others can build to their needs.
Thx,
Martin politick.

---

### Post by handy on 2011-08-18
You can access the internet & mobile phones with the Arduino systems in a variety of ways both wired & wireless:- you can talk to a web server; send email; SMS, & more.

---

