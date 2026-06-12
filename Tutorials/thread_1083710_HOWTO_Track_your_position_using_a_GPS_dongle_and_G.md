---
title: "HOWTO: Track your position using a GPS dongle and Google Earth"
date: 2009-03-01
forum: Tutorials
---

### Post by daved2424 on 2009-03-01
This tutorial is designed to guide you through doing exactly what the title says it does. I must profess I am **not** an expert and have only been using a Linux based system for a couple of weeks. As a result I will more than likely struggle to answer any of your questions, but I will endevour none the less to help as much as I can anyway.

The method described below was carried out on an 900 Eee PC running Easy Peasy (I could not get this to work using Eeebuntu). Most of the information is from third party sources that I have cobbled together into this one tutorial, references wherever possible.

Please point out any mistakes. I will try and adapt it at some point to draw polylines as well.



[SIZE="6"][FONT="Arial"][SIZE="4"]**_1. Install Google Earth_**[/SIZE][/FONT][/SIZE]
[LIST=1]
[*]Download Google Earth from the [_[COLOR="Blue"]Google Earth Website[/COLOR]_]("http://earth.google.com/"). I am running v4.3 as my Eee is only wee. This can be chosen on the second page of the download process.

[*]Save the file to your desktop and call it GoogleEarthLinux.bin.

[*]Open terminal and type the following three lines one at a time:

```
[INDENT]cd ~/Desktop

chmod +x GoogleEarthLinux.bin

sudo ./GoogleEarthLinux.bin[/INDENT]
```

[*]Leave the default options and click **Begin Install**.

[*]Once it has finished click **Quit** not **Start** as this will run the programme as root which is not a good idea.

[*]Check that Google Earth works. Under Applications => Internet. To get the best results from GE turn Atmosphere off: View => Atmosphere.

[*]Delete the bin file on the desktop and close terminal.

[_[COLOR="Blue"]Reference[/COLOR]_]("https://help.ubuntu.com/community/GoogleEarth")
[/LIST]


[SIZE="6"][FONT="Arial"][SIZE="4"]**_2. Pairing With Bluetooth GPS Dongle_**[/SIZE][/FONT][/SIZE]
[LIST=1]
[*]Enable Bluetooth on you machine. If you do not have built-in bluetooth (like my Eee), then you will need a USB dongle; a couple of quid from eBay.

[*]It is likely that you will not be able to pair your device using the bluetooth wizard as there is unlikely you will be able to enter a passcode on your dongle. So we need to get it to do it the other way round. Re-open terminal and scan for the device using:

```
[INDENT]hcitool scan
[/INDENT]
```

[*]Write down the MAC address of your GPS dongle. For example 03:3F:AE:98:00:DA.
[*]Enable the authentication of your GPS dongle with the following line. Note: no response will be printed within terminal.

```
[INDENT]sudo hciconfig hci0 auth
[/INDENT]
```

[*]Create a connection with the device:

```
[INDENT]sudo hcitool cc 03:3F:AE:98:00:DA
[/INDENT]
```

[*]A pop-up will appear asking you to enter the PIN for your dongle. This should be somewhere in your original documentation. If you don't have it try something generic like 0000, 1111 or 1234.
[*]Click on the bluetooth icon in the menu bar top-right and see how you now have a pairing.

[_[COLOR="Blue"]Reference[/COLOR]_]("https://lists.ubuntu.com/archives/ubuntu-bluetooth/2008-December/003046.html")
[/LIST]


[SIZE="6"][FONT="Arial"][SIZE="4"]**_3. Edit rfcomm.conf_**[/SIZE][/FONT][/SIZE]
[LIST=1]

[*]In terminal type the following:

```
[INDENT]sudo gedit /etc/bluetooth/rfcomm.conf
[/INDENT]
```

[*]This will open the file as the root user and allow you to make changes.
[*]Add the following lines to the bottom of the file:

```
[INDENT]rfcomm4 {
bind no;
device 03:3F:AE:98:00:DA;
channel 1;
comment "GPS Bluetooth Dongle";
[/INDENT]
```

[*]Save the file.

[_[COLOR="Blue"]Reference[/COLOR]_]("http://blogs.srijan.in/2008/01/19/bluetooth-gps-devices-with-linux/#hcid.conf")
[/LIST]


[SIZE="6"][FONT="Arial"][SIZE="4"]**_4. Establish the RF Communication_**[/SIZE][/FONT][/SIZE]
[LIST=1]

[*]In a new terminal window type the following:

```
[INDENT]sdptool add --channel=1 OPUSH
[/INDENT]
```

[*]This should return something like:

```
[INDENT]OBEX Object Push service registered
[/INDENT]
```

[*]Now type the following:

```
[INDENT]sudo rfcomm bind /dev/rfcomm4 03:3F:AE:98:00:DA
[/INDENT]
```

[_[COLOR="Blue"]Reference[/COLOR]_]("http://blogs.srijan.in/2008/01/19/bluetooth-gps-devices-with-linux/#hcid.conf")
[/LIST]


[SIZE="6"][FONT="Arial"][SIZE="4"]**_5. Read Data from the GPS Dongle_**[/SIZE][/FONT][/SIZE]
[LIST=1]

[*]In terminal type the following:

```
[INDENT]cat /dev/rfcomm4
[/INDENT]
```

[*]You should see a steady stream of data being read from the GPS device.

[_[COLOR="Blue"]Reference[/COLOR]_]("https://lists.ubuntu.com/archives/ubuntu-bluetooth/2008-December/003046.html")
[/LIST]


[SIZE="6"][FONT="Arial"][SIZE="4"]**_6. Create KML File_**[/SIZE][/FONT][/SIZE]
[LIST=1]

[*]Create a new folder to keep the KML file in:

```
[INDENT]sudo mkdir /opt/google-earth/realtime
[/INDENT]
```

[*]Open text Editor as root user. In terminal type:

```
[INDENT]sudo gedit
[/INDENT]
```

[*]Copy and paste the following code:

```
[INDENT]<?xml version="1.0" encoding="UTF-8"?>
<kml xmlns="http://earth.google.com/kml/2.2">
<NetworkLink>
	<name>Realtime GPS</name>
	<open>1</open>
	<Link>
		<href>./realtime/Realtime GPS.kml</href>
		<refreshMode>onInterval</refreshMode>
	</Link>
</NetworkLink>
</kml>
[/INDENT]
```

[*]Save the file as **/opt/google-earth/realtime/Realtime GPS.kml**
[*]Navigate to the file using File Browser and double-click it. It should automatically open up in Google Earth. In the "Places" section on the right the KML file will be listed under Temporary places. To make the KML file available everytime you load Google Earth right-click it and select "Add to my places".
[*]Right-click the XML in Google Earth and create a Network link to the KML file on your hard drive.

[_[COLOR="Blue"]Reference[/COLOR]_]("http://tjworld.net/wiki/Linux/Ubuntu/GoogleEarthPlusRealTimeGPS")
[/LIST]


[SIZE="6"][FONT="Arial"][SIZE="4"]**_7. Create GPS Data Server_**[/SIZE][/FONT][/SIZE]
[LIST=1]

[*]For this part you will need to find out the baud rate of your GPS dongle. This should be included in the technical specification for the device. Failing that contact the manufactuer directly. My baud rate is 38400.
[*]Install the python serial package from terminal:

```
[INDENT]sudo apt-get install python-serial
[/INDENT]
```

[*]Open Text Editor as root user again from terminal (sudo gedit).
[*]Copy and paste the following code into the file:

```
[INDENT]#!/usr/bin/python

# Copyright (C) 2007 by Jaroslaw Zachwieja <grok!warwick.ac.uk>
# Copyright (C) 2008 by TJ <linux!tjworld.net>
# Published under the terms of GNU General Public License v2 or later.
# License text available at http://www.gnu.org/licenses/licenses.html#GPL

import serial
import string
import sys
import getopt

def usage():
		print "Usage:"
		print " -p | --port <device>   e.g. /dev/rfcomm4"
		print " -b | --baud <speed>    e.g. 38400"
		print " -f | --file <filename> e.g. /opt/google-earth/realtime/Realtime GPS.kml"
		print " -h | --help     display options"

def main():
	# defaults
	serial_port = "/dev/rfcomm4"
	serial_baud = 38400
	file = '/opt/google-earth/realtime/Realtime GPS.kml'

	try:
		opts, args = getopt.getopt(sys.argv[1:], "p:b:f:h", ["port=", "baud=", "file=", "help"])
	except getopt.GetoptError:
		usage()
		sys.exit(1)
	else:
		for opt, arg in opts:
			if opt in ("-p", "--port"):
				serial_port = arg
			elif opt in ("-b", "--baud"):
				serial_baud = string.atof(arg)
			elif opt in ("-f", "--file"):
				file = arg
			elif opt in ("-h", "--help"):
				usage()
				sys.exit(0)
			else:
				print "Unknown option"

	gps = serial.Serial(serial_port, serial_baud, timeout=1)

	print "Serving data from %s (%d baud) to %s" % (serial_port, serial_baud, file)

	latitude = 0
	longitude = 0
	speed = 0
	heading_in = 0
	altitude = 0
	range = 1000
	tilt = 30

	while 1:
		line = gps.readline()
		datablock = line.split(',') 

		if line[0:6] == '$GPRMC':
			latitude_in = string.atof(datablock[3])
			longitude_in = string.atof(datablock[5])
			try:
				altitude = string.atof(datablock[8])
			except ValueError:
				# use last good value
				altitude = altitude
			speed_in = string.atof(datablock[7])
			try:
				heading_in = string.atof(datablock[8])
			except ValueError:
				# use last good value
				heading_in = heading_in
			if datablock[4] == 'S':
				latitude_in = -latitude_in
			if datablock[6] == 'W':
				longitude_in = -longitude_in

			latitude_degrees = int(latitude_in/100)
			latitude_minutes = latitude_in - latitude_degrees*100

			longitude_degrees = int(longitude_in/100)
			longitude_minutes = longitude_in - longitude_degrees*100

			latitude = latitude_degrees + (latitude_minutes/60)
			longitude = longitude_degrees + (longitude_minutes/60)

			speed = int(speed_in * 1.852)
			range = ( ( speed / 100  ) * 350 ) + 650
			tilt = ( ( speed / 120 ) * 43 ) + 30
			heading = heading_in

			if speed < 10:
				range = 200
				tilt = 30
				heading = 0

			output = """<?xml version="1.0" encoding="UTF-8"?>
	<kml xmlns="http://earth.google.com/kml/2.0">
		<Placemark>
			<name>%s km/h</name>
			<description>^</description>
			<LookAt>
				<longitude>%s</longitude>
				<latitude>%s</latitude>
				<range>%s</range>
				<tilt>%s</tilt>
				<heading>%s</heading>
			</LookAt>
			<Point>
				<coordinates>%s,%s,%s</coordinates>
			</Point>
		</Placemark>
	</kml>""" % (speed,longitude,latitude,range,tilt,heading,longitude,latitude,altitude)

			f=open(file, 'w')
			f.write(output)
			f.close()

	ser.close()

if __name__ == "__main__":
	main()
[/INDENT]
```

[*]Save the file as **/opt/google-earth/gegpsd.py**
[*]Now this file needs to be made executable:

```
[INDENT]sudo chmod +x /opt/google-earth/gegpsd.py
[/INDENT]
```

[_[COLOR="Blue"]Reference[/COLOR]_]("http://tjworld.net/wiki/Linux/Ubuntu/GoogleEarthPlusRealTimeGPS")
[/LIST]


[SIZE="6"][FONT="Arial"][SIZE="4"]**_8. Create Application Launcher_**[/SIZE][/FONT][/SIZE]
[LIST=1]

[*]Lastly we need to create an application launcher that will execute the commands to get all the above working in one go each time you use it. Open Text Editor as root user again (sudo gedit in Terminal). Copy and paste the following code:

```
[INDENT]#!/bin/bash

sdptool add --channel=1 OPUSH
sudo rfcomm bind /dev/rfcomm4 03:3F:AE:98:00:DA
/opt/google-earth//googleearth %f
sudo /opt/google-earth/gegpsd.py
exit
[/INDENT]
```

[*]Save the file as **/opt/google-earth/gps-track.sh**.
[*]Give the file the right privaleges. In terminal:

```
[INDENT]sudo chmod a+x /opt/google-earth/gps-track.sh
[/INDENT]
```

[*]Now we will create a shortcut to it from your application menu. Open the Main Menu application: **Preferences => Main Menu**
[*]Select "Internet" on the left and then "New Item" on the right.
[*]Enter the following information: Type- Application in Terminal; Name- Google Earth Track; Command- /opt/google-earth/gps-track.sh; Comment- Real-time GPS Tracking in Google Earth.
[*]If you want the SVG version of the Google Earth icon one can be found [_[COLOR="Blue"]here[/COLOR]_]("http://svgicons.o7a.net/official.svg"), but you can work out how to do that bit for yourself.
[*]Hit close and check to see if it is in your applications menu.
[*]Remove your USB bluetooth dongle and restart the machine.
[*]Once it has loaded, plug in your USB dongle and launch Google Earth Track from the applications menu. **Note:** you have have to select Google Earth Track the first time you run Google Earth after the computer has finished booting.
[*]You will be required to enter your sudo password in terminal. If anyone knows of a way to get around this please post below.
[*]You should now be good to go!
[/LIST]

---

### Post by daved2424 on 2009-05-20
If you find yourself having trouble with the application launcher try opening terminal instead and typing in the following:

```
[INDENT]
sdptool add --channel=1 OPUSH
sudo rfcomm bind /dev/rfcomm4 03:3F:AE:98:00:DA
sudo /opt/google-earth/gegpsd.py
exit
[/INDENT]
```

Now try running Google Earth. This is technique is instead of using the application launcher.

---

### Post by linuxtechie on 2011-01-02
^ I haven't tried it yet, but let me thank you in advance.

+LT

---

### Post by bkpsusmitaa on 2012-07-13
Dear friends,
O tried the codes, everything works in pieces, but we have a failure
> 
  File "/opt/google/earth/gegpsd.py", line 14
    print "Usage:"
        ^
IndentationError: expected an indented block

Hope the problem will be identified.

---

### Post by Xinv3rse on 2012-07-14
This sounds interesting and awesome. I'll try it as soon as my browser bug gets resolved.

---

### Post by bkpsusmitaa on 2012-07-15
Please visit my Debian page and read the posting there. The link is:
[http://forums.debian.net/viewtopic.php?f=7&t=81806&p=443485#p443485](http://forums.debian.net/viewtopic.php?f=7&t=81806&p=443485#p443485)

I have nearly to my destination, but am faltering at the final step. The present version of google earth for Linux is > Google Earth 6.2.2.6613
Build Date 4/14/2012
Build Time 1:09:13 am
Renderer OpenGL
Operating System Linux (2.6.32.0)
Video Driver NVIDIA Corporation
Max Texture Size 8192x8192
available video memory 512 MB
Server kh.google.comI write my experiences below:
```
##A test of how to activate each command only after the earlier command has ended its work###

#release earlier record of bluetooth devices if any. Service Discovery Protocol:
#The process of searching for services involves two steps - detecting all nearby devices with a device inquiry, and connecting to each of those devices in turn to search for the desired service. sdptool — control and interrogate SDP servers

sdptool del record_handle

#Radio frequency communication (RFCOMM) see wikipedia
The Bluetooth protocol RFCOMM is a simple set of transport protocols, made on top of the L2CAP protocol, providing emulated RS-232 serial ports (up to sixty simultaneous connections to a Bluetooth device at a time). The protocol is based on the ETSI standard TS 07.10. RFCOMM is sometimes called serial port emulation. The Bluetooth serial port profile is based on this protocol. RFCOMM provides a simple reliable data stream to the user, similar to TCP. It is used directly by many telephony related profiles as a carrier for AT commands, as well as being a transport layer for OBEX over Bluetooth.
Many Bluetooth applications use RFCOMM because of its widespread support and publicly available API on most operating systems. Additionally, applications that used a serial port to communicate can be quickly ported to use RFCOMMrfcomm is used to set up, maintain, and inspect the RFCOMM configuration of the Bluetooth subsystem in the Linux kernel. If no command is given, or if the option -a is used, rfcomm prints information about the configured RFCOMM devices.
rfcomm release /dev/rfcomm4 00:0D:B5:82:A1:EB

# Enable the authentication of  (of the computer) with the following line. Host/controller interface (HCI) is the Standardised communication between the host stack (e.g., a PC or mobile phone OS) and the controller (the Bluetooth IC). This standard allows the host stack or controller IC to be swapped with minimal adaptation. No response will be printed. hciconfig - configure Bluetooth devices. hciX is the name of a Bluetooth device installed in the system. If hciX is not given, "hciconfig" prints name and basic information about all the Bluetooth devices installed in the system. Suppose your bluetooth device (the first one is which is in-built in computer) is hci0, then
hciconfig hci0 down
hciconfig hci0 up
hciconfig hci0 noauth
hciconfig hci0 auth

#hcitool - configure Bluetooth connections.
# To display local devices
hcitool dev

#To inquire remote devices. For each discovered device, device name are printed.
hcitool scan

# Create a connection of the computer bluetooth device with the GPS dongle device. Remember to repeat, because the first time gives Input/output error, because the system is asking for a pairing code.
hcitool cc 00:0D:B5:82:A1:EB


# Establish the RF Communication
sdptool add --channel=1 OPUSH
rfcomm bind /dev/rfcomm4 00:0D:B5:82:A1:EB

cat /dev/rfcomm4

/opt/google/earth/free//googleearth %f
/opt/google/earth/gegpsd.py
exit
```It secures a stable connection, and starts google Earth. 
> /opt/google/earth/free//googleearth %f
I shut down the Google Earth by clicking on the "X" option. I get an output:
> Segmentation faultThen the last line of the code is executed and I get the following final output on the root terminal.
> 
root@Squeeze:/home/user# /opt/google/earth/gegpsd.py
Serving data from /dev/rfcomm4 (38400 baud) to /opt/google/earth/realtime/Realtime GPS.kml
When I kill the data serving by control+C, I get,
> ^CTraceback (most recent call last):
  File "/opt/google/earth/gegpsd.py", line 124, in <module>
    main()
  File "/opt/google/earth/gegpsd.py", line 58, in main
    line = gps.readline()
  File "/usr/lib/python2.6/dist-packages/serial/serialutil.py", line 60, in readline
    c = self.read(1)
  File "/usr/lib/python2.6/dist-packages/serial/serialposix.py", line 317, in read
    ready,_,_ = select.select([self.fd],[],[], self._timeout)
KeyboardInterrupt
Trouble is: How to let google earth catch this GPS data?

Combination of both the two commands do not help either:
> /opt/google/earth/free//googleearth %f|/opt/google/earth/gegpsd.py
What does the %f code-bit stand for?

---

### Post by teejayevans on 2013-09-05
I use GPSD (allows me to skip steps 2-5) so I put this together, works for me, YMMV:
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/file.h>
#include <signal.h>
#include <gps.h>

/**
  Used python code by TJ and Jaroslaw Zachwieja as model to create KML (esp: range/tilt values)
  wrote this to use GPSD server to handle low level GPS/serialport work
  I used GPSD v3.9, libgps.so was linked to libgps.so.20.0.0 in /usr/local/lib
  to build: cc -o kmlgps -L/usr/local/lib -lgps kmlgps.c
**/
static struct gps_data_t GPS;
static struct gps_data_t *gps=&GPS;
static char *ofn="/opt/google/earth/realtime/Realtime_GPS.kml";
static char *outfile = NULL;

void gps_handler(struct gps_data_t *sent, char *buf, size_t len, int level)
{
  printf("GPSD: %s\n", buf);
  fflush(stdout);
}

void dump_state(struct gps_data_t *collect)
{
  float latitude_in = 0.0;
  float longitude_in = 0.0;
  float speed_in = 0.0;
  float heading_in = 0.0;
  float altitude_in = 0.0;
  int	range = 1000;
  int	tilt = 30;
  // check if data is a valid fix
  if (((collect->set & STATUS_SET) && collect->status>0) && 
      ((collect->set & MODE_SET) && collect->fix.mode>1))
    {
    if (collect->set & LATLON_SET) {
      latitude_in=collect->fix.latitude; 
      longitude_in=collect->fix.longitude;
    }
    if (collect->set & ALTITUDE_SET)
      altitude_in=collect->fix.altitude;
    if (collect->set & SPEED_SET)
      speed_in=collect->fix.speed;
    if (collect->set & TRACK_SET)
      heading_in=collect->fix.track;
    }
  // from python code, they didn't explain the math. I just copied it 
  int speed = (int)(speed_in * 1.852);
  range = ( ( speed / 100  ) * 350 ) + 650;
  tilt = ( ( speed / 120 ) * 43 ) + 30;
  int heading = (int)heading_in;
  if (speed < 10) {
    range = 200;
    tilt = 30;
    heading = 0;
  }
  if (outfile==NULL) outfile=ofn;
  int fd = open(outfile, O_WRONLY | O_CREAT , 0640);
  if (fd < 0) {
    perror("open");
    exit(3);
  }
  FILE *fp = fdopen(fd, "w");
  if (fp==NULL) {
    perror("fdopen failed");
    exit(4);
  }

  rewind(fp);
  char buf[4096];
  sprintf(buf,"<?xml version=\"1.0\" encoding=\"UTF-8\"?>\n<kml xmlns=\"http://earth.google.com/kml/2.0\">\n<Placemark>\n<name>%d km/h</name>\n<description>GPSD placemark</description>\n<LookAt>\n<longitude>%.6f</longitude>\n<latitude>%.6f</latitude>\n<range>%d</range>\n<tilt>%d</tilt>\n<heading>%d</heading>\n</LookAt>\n<Point>\n<coordinates>%.6f,%.6f,%.2f</coordinates>\n</Point>\n</Placemark>\n</kml>\n",speed,longitude_in,latitude_in,range,tilt,heading,longitude_in,latitude_in,altitude_in);
  fwrite(buf, strlen(buf), 1, fp);
  fputc('\n', fp);
  fclose(fp);
}

void initfile() {
  if (outfile==NULL) outfile=ofn;
  int fd = open(outfile, O_WRONLY | O_CREAT , 0640);
  if (fd < 0) {
    perror("open");
    exit(3);
  }

  FILE *fp = fdopen(fd, "w");
  if (fp==NULL) {
    perror("fdopen failed");
    exit(4);
  }
  rewind(fp);
  char buf[1024];
  sprintf(buf,"<?xml version=\"1.0\" encoding=\"UTF-8\"?>\n<kml xmlns=\"http://earth.google.com/kml/2.2\">\n<NetworkLink>\n<name>Realtime GPS</name>\n<open>1</open>\n<Link>\n<href>%s</href>\n<refreshMode>onInterval</refreshMode>\n</Link>\n</NetworkLink>\n</kml>\n", outfile);
  fwrite(buf, strlen(buf), 1, fp);
  fputc('\n', fp);
  fclose(fp);
  printf("open this file (%s) with google-earth, it will be listed under Temporary places, add it my places, then create a network link to this file, you only have to do this once", outfile);
  exit(0);
}

void usage(char *progname) {
  printf("%s [-s machinename] [-p netport] [-w wait] [-f filename] [-i]\n", progname);
  printf("\t-f filename\tThe full path to KML file (default /opt/google/earth/realtime/Realtime_GPS.kml)\n");
  printf("\t-s machinename\tThe GPSD server IP address (default 127.0.0.1)\n");
  printf("\t-p netport\tSpecifiy GPSD port# (default 2947)\n");
  printf("\t-w waittime\tPoll gps data period in msec (default 5000)\n");
  printf("\t-i initialize flag\tCreate init file, must link via google-earth\n");
}

void
termination_handler (int signum)
{
  fprintf(stderr,"Signal %d received, kmlgps terminating\n", signum);
  (void) gps_stream(gps, WATCH_DISABLE, NULL);
  (void) gps_close (gps);
  exit(0);
}

int main(int argc, char *argv[])
{
  char *server="127.0.0.1";
  char *port="2947";
  int wait = 5000; // 5 sec
  int c;
  extern char *optarg;
  int initflag=0;

  while ( (c=getopt(argc,argv,"i?f:p:s:w:")) != EOF )
    switch (c) {
    case 'i':
      initflag=1;
      break;
    case 'f':
      outfile=optarg;
      break;
    case 's':
      server=optarg;
      break;
    case 'p':
      port=optarg;
      break;
    case 'w':
      wait=atoi(optarg);
      break;
    case '?':
      usage(argv[0]);
      exit(1);
    }
  if (initflag>0) initfile();

  if (signal (SIGINT, termination_handler) == SIG_IGN)
    signal (SIGINT, SIG_IGN);
  if (signal (SIGHUP, termination_handler) == SIG_IGN)
    signal (SIGHUP, SIG_IGN);
  if (signal (SIGTERM, termination_handler) == SIG_IGN)
    signal (SIGTERM, SIG_IGN);


  memset(gps,0,sizeof(GPS));
  //printf("gps_data_t size %d\n",sizeof(GPS)); // is 6920 for me
  
  int fd = gps_open(server, port, gps);
  if(fd<0)
    {
      perror("gpsd server not found");
      exit(1);
    }
  
  (void) gps_stream(gps, WATCH_ENABLE | WATCH_JSON, NULL);
  
  while(1) {
    if (gps_waiting (gps, wait)) { //in msecs
      if (gps_read (gps) == -1) {
	perror("gps_read");
      } else {
	dump_state(gps);
      }
    }
  } 
  return 0;
}


```

---

