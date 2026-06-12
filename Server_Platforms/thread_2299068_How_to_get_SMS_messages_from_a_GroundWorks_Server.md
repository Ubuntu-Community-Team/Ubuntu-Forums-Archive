---
title: "How to get SMS messages from a GroundWorks Server?"
date: 2015-10-15
forum: Server Platforms
---

### Post by aaron27 on 2015-10-15
I am trying to setup a linux machine (Ubuntu 12.04 64bit) to send out SMS messages from a Nokia phone (Nokia E50) plugged in via USB through Gnokii.The end result of this being that Groundworks notifications will be sent  via SMS even when our exchange server is down, if anyone knows an  alternative to using Gnokii then please advise.

I  have downloaded/installed Gnokii, having edited the gnokiirc file  (Posted below) I then try to run the command and send an SMS but get  this error message( I have also run this as sudo) :

```

ERROR MESSAGE.

user@server:~$ echo "gnokii test" | gnokii --sendsms 'mobile number entered here'

GNOKII Version 0.6.30

Couldn't read /home/groundwork/.config/gnokii/config config file
Couldn't read /etc/xdg/xdg-gnome-shell/gnokii/config config file
Gnokii serial_open: open: Permission denied
Couldn't open FBUS device: Permission denied
Gnokii serial_open: open: Permission denied
Couldn't open FBUS device: Permission denied
Gnokii serial_open: open: Permission denied
Couldn't open FBUS device: Permission denied
Telephone interface init failed: Command failed.

Quitting.
Command failed.


```

So  obviously I know there are some permission errors there (not sure where  I am supposed to change the permissions though). And I also tried to  find the two files that couldn't be read, in order to edit them and/or change permissions, however they do not exist. 

The  command I ran to install gnokii was sudo apt-get install gnokii which completed with no errors.

Please see below the content of my gnokiirc file, which is in both the Home folder and is also located in the /etc location (as per gnokii's instructions).

```


# This is a sample ~/.gnokiirc file. Copy it into your
# home directory and name it .gnokiirc.
# See http://wiki.gnokii.org/index.php/Config for working examples.
#

[global]

# Set port to the physical port used to connect to your phone.
# Linux version is:
#port = /dev/ttyACM0
#
# For MacOSX you will need something like:
# port = /dev/cu.USA28X1P1.1
#
# For Win32 you want to use:
# port = com1:
# or similiar.
#
# FreeBSD (probably NetBSD and OpenBSD too) use:
# port = /dev/cuaa0
#
# With Linux-IrDA you will want to use
# port = /dev/ircomm0
# or similiar.
#
# Use this setting also for the Bluetooth connection:
# port = aa:bb:cc:dd:ee:ff
# when using it with AT driver set it to:
#port = /dev/rfcomm0
# or similiar.
#
# For the Linux USB cables you will need one of the following settings (or
# similiar)
# port = /dev/ttyUSB0
#port = /dev/tts/USB0
# port = /dev/ttyACM0
# the last one will work only with AT driver. The correct setting should be
# given in the dmesg output.
#
# If you use connection type dku2libusb use it to denote which use endpoint
# you'd wish to use. It is useful when you have more than one phone connected
# to your computer using DKU2 cable. Numbering goes from 1 upwards.
# Default is 1.
# port = 1

# Set model to the model number of your phone. For the
# Symbian phones use:
# model = Nokia
# For other non-Nokia phones and when you want to use AT
# mode use:
model = AT
# If you can't figure out what to put here read the FAQ.
# If it still doesn't help, consult gnokii-ml or #gnokii at freenode.
#model = 2700
# There are few main models that should make use of the certain drivers.
# These are: 6110, 7110, 6510, 3110, 2110, 6160.

# Set IrDA device name.
# If you use irda connection you may want gnokii to autodetect the irda
# device it connects to. This is fine for most of the cases. if you have
# more than one device in range you may want to give manually the device
# name so gnokii correctly recognizes it. Use the name that you can see
# in the discovery log when the phone with infrared is in the range of
# your irda port.
# Note that you need to set this for each phone_ section separately. It
# isn't nested from the global section.
# irda_string = Nokia E50

# Initlength controls the number of characters sent to the
# phone during initialisation. You can either set it to
# the word "default" or a positive integer.
#
# You can try setting this value if you want to connect
# to the phone quicker. If you've never noticed the
# connection to be slow, it is suggested that you
# leave this alone. Read the initialisation code in fbus-xxxx
# to understand what this changes if you're curious.
initlength = default

# The type of the connection, for IR set this to infrared or irda.
# For the nk6110 driver only infrared is valid for the IrDA connection.
# See Docs/gnokii-ir-howto for more detailes on this.
# If you have 6210/6250/7110 phone and dau9p cable (the one you can
# use with 6100 series and cannot use hardware modem from the phone)
# you may want to use 'dau9p' value to get faster initialization.
# If you use dlr3 or dlr3p cable for nokia phones in FBUS mode (ie.
# you don't use model = AT) you may want to use 'dlr3p' value here.
# Note that it is recommended and currently the best way to use this
# cable with nk6510 driver.
#connection = dau9p
# With DKU-2 cable use the following setting if you want to libusb driver
# (recommended):
# connection = dku2libusb
# or the following setting if you want to use Linux kernel driver
# connection = dku2
# With DKU-5 cable use the following setting
# connection = dku5
# For Bluetooth and AT driver use the following setting
connection = serial
# For other Bluetooth settings use
# connection = bluetooth
# For infrared connection with phones other than Nokia 6110/6130/6150 use:
# connection = irda
# Don't forget to run: 'irattach irda0 -s' or similiar before running gnokii
# For connection with a PC/SC compatible Smart Card reader use:
# connection = pcsc

# Set this to 'yes' if you want gnokii to set and check the lock file in
# /var/lock directory. It avoids potential conflicts with other serial
# port software (eg. minicom). If you have wrong permissions for the
# directory, a warning will be generated. If you don't want a lockfile, set
# it to 'no'.
use_locking = no

# Baudrate to use on serial port connections.
# Currently used only by models AT and BIP/CIMD. Defaults to 19200.
serial_baudrate = 9600

# Force waiting after each send character the specified usec time.
# Value -1 forces the fastest 'block' writing,
# value 0 writes each character separately without any explicite waiting,
# other positive values specify the appropriate 1/1000000 sec delaying.
# Siemens M20 requires at least "1"! FIXME: Model-driven autodetection
#serial_write_usleep = -1

# Force serial port handshaking mode, useful primarily for "AT" model.
# Gnokii "AT" model uses software handshake by default.
# Possible values: hardware (RTS/CTS - 7 wires) or software (XON/XOFF - 3 wires)
#handshake = software

# If defined (not commented out by '#') it will quit Gnokii anytime
# when DCD line will drop.
#require_dcd = 0

# If you are using a bluetooth connection, you can specify the rfcomm
# channel number here. Default value is 1.
#rfcomm_channel = 1

# There may happen various timeouts during the communication with the phone.
# This parameter enables the retransmission policy. Ie. if the phone doesn't
# respond, we send the frame again. This happened mainly with the older
# phones. You may want to enable it when you see mysterious timeouts.
# Be very careful with this option. It is suspected to cause phone breakage
# with new DCT4 phones (like Nokia 6100). By default it is switched off
# (sm_retry = 0)
#sm_retry = 0

# Run the specified script(s) right after opening and initializing the device
# and before any communication (right before closing for disconnect_script).
# You may find handy to use it to connect your modem to SMS Center
# when using BIP or CIMD protocols
# Non-absolute path is relative to the specific directory where gnokii is run!
#connect_script = /absolute/path/to/gnokii/Docs/sample/cimd-connect
#disconnect_script =

# When sending SMS you can experience timeouts. This is the feature of the
# overloaded SMSCs. The phones waits for the response from the SMSC confirming
# that it received the short message. When the SMSC is DoSed with many requests
# it will take more time to get the response. Adjust it to your needs. The
# value is given in seconds to wait. Defaults to 10 seconds. Set to 0 to wait
# forever.
smsc_timeout = 10

# Set this to 1 if you want to break your phone with xgnokii. Works only
# with few Nokia models and FBUS communication
[xgnokii]
allow_breakage = 0

# Set bindir to point to the location of the various gnokiid binaries.
# In particular ensure that mgnokiidev is in this location, with
# permissions 4750, owned by root, group gnokii. Ensure you
# are in the gnokii group and that the group exists...
[gnokiid]
bindir = /usr/sbin/

# Any entries in the following two sections will be set as environment
# variables when running the scripts.
# Handy for use for $VAR substitutions in your chat(8) script.
[connect_script]
TELEPHONE = 12345678
[disconnect_script]


# The following parameters control how libgnokii handles the debugging messages.
# Currently there are three categories: "debug" controls the libgnokii
# normal debug output, "rlpdebug" controls the debug output of the RLP
# subsystem, and "xdebug" is used by the xgnokii or smsd.

[logging]

# where to log the debug output (on: stderr, off: /dev/null)
debug = off

# where to log the rlp debug output (on: stderr, off: /dev/null)
rlpdebug = off

# where to log X debug output (on: stderr, off: /dev/null)
xdebug = off


```

Please note this post is also posted here: [http://serverfault.com/questions/729197/gnokii-sms-issue](http://serverfault.com/questions/729197/gnokii-sms-issue)

---

### Post by tgalati4 on 2015-10-15
You might need to uncomment one of these options.

> # For the Linux USB cables you will need one of the following settings (or
# similiar)
# port = /dev/ttyUSB0
#port = /dev/tts/USB0
# port = /dev/ttyACM0


On 14.04 the USB port is typically /dev/ttyS0.  Verify on your system and give it open permissions if it still doesn't work:

```
sudo chmod 777 /dev/ttyS0
```

The missing configuration files may be OK as long as you have at least one somewhere on the path.

---

### Post by aaron27 on 2015-10-15
Thank you for your reply, I have done as suggested and I now get this:

```
GNOKII Version 0.6.30

Couldn't read /home/groundwork/.config/gnokii/config config file
Couldn't read /etc/xdg/xdg-gnome-shell/gnokii/config config file         
Telephone interface init failed: Command timed out.
Quitting.
Command timed out.
```

This is the same as what I get if I run the command 'su root' and then try to run the command.

---

### Post by tgalati4 on 2015-10-15
Try uncommenting:

```
model = Nokia
```

I have not set up *gnokii*, nor do  I have a Nokia E50  phone.  It appears that the phone is not responding to modem "AT" commands.

Comment out the "AT" command line.

Try each Nokia model (6110, 7110, 6510, 3110, 2110, 6160) until something works.  Take notes.  If you have two gnokii configuration files, delete one and use the one in /etc only.  Having two configuration files only confuses things.

Post the output of /etc/.gnokiirc

Your phone may not work through a USB cable:

> Symbian series60 3rd edition (most Nokia n and e series) are not supported by gnapplet driver due to changes in Symbian API. For now you can get some functionality using AT driver.

What exactly are you trying to do?  There might be a better way to get a server to send a text message.

---

### Post by aaron27 on 2015-10-15
Ok thank you for the advice, still no luck yet but I am persisting.

We run groundworks which sends emails via our exchange, we want a fail safe in case exchange goes down. We had it running previously on a server with a nokia plugged in (different model) and it used gnokii to send sms messages. we have since upgraded the server and to the latest version of groundworks. If you know a way we can get the notifications via SMS that is different I am all ears (the only restriction being it cant require exchange)

---

### Post by tgalati4 on 2015-10-15
Find that old phone!  

Some ideas:  [https://bbs.archlinux.org/viewtopic.php?id=67388](https://bbs.archlinux.org/viewtopic.php?id=67388)

*smsclient* needs a phone line or way to dial out.  I don't know if gmail still supports SMS texting through their server.  Many phone providers have their own email-to-SMS server.  Just use *postfix* or some other backup mailer for your messages.

Your title should change to:  *How to get SMS messages from a GroundWorks Server?*  

Who is your Cell Phone carrier?   I use ATT and use the following:

> To send a text, picture, or video message1 to an AT&T wireless device from your email:
Text message: Compose a new email and use the recipient's 10-digit wireless phone number, followed by @txt.att.net. For example, [email]5551234567@txt.att.net[/email].
Picture or video message: Compose a new email and use the recipient's 10-digit wireless phone number, followed by @mms.att.net. For example, [email]5551234567@mms.att.net[/email].
Don't include dashes or spaces in between the numbers.

---

### Post by aaron27 on 2015-10-16
Have edited the post a bit as advised.
smsclient is no good as we dont have a modem to use.

---

### Post by coldraven on 2015-10-16
Have you looked at gammu? Some time ago I used it to backup and restore my old Nokias via Serial or Bluetooth. I never tried sending SMS but I just read that it has a SMS daemon that might work for you. I notice that the Gammu page has been updated this year but the Gnokki page was last updated in 2011.
Gammu is in the the repos.
[http://wammu.eu/docs/manual/](http://wammu.eu/docs/manual/)

---

### Post by aaron27 on 2015-10-19
I seem to be making some progress with Gnokii and now instead of getting:

```

GNOKII Version 0.6.30

Couldn't read /home/groundwork/.config/gnokii/config config file
Couldn't read /etc/xdg/xdg-gnome-shell/gnokii/config config file         
Telephone interface init failed: Command timed out.
Quitting.
Command timed out.
```

I get:

```

GNOKII Version 0.6.30

Couldn't read /home/groundwork/.config/gnokii/config config file     
Telephone interface init failed: Command timed out.
Quitting.
Command timed out.
```

---

### Post by aaron27 on 2015-10-19
It would of course help if the phone was picked up by Linux... which I am looking into now

---

