---
title: "Mgetty not answering"
date: 2010-07-20
forum: Server Platforms
---

### Post by dalitso on 2010-07-20
I have an external USB  56k soft modem that came with linux drivers. It&#8217;s got conexant chipset. I successfully installed the drivers on my Ubuntu 8.04 box. 

I want to dialin to my server using this modem so I installed mgetty. The problem is that mgetty is not answering  a call when I dial to the phone number . 

I have only one phone line which is also my ADSL line so I am using a cell phone to dial to my telephone number this modem is connected to.

If I implement the same exact setup on my debian box, it is working, mgetty is answering the call. I even went to a friend and used his phone line and I connected to the debian box using Hyperterminal.
Here are my configs and outputs

```

root@wani:~# lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0572:1329 Conexant Systems (Rockwell), Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

```

root@wani:~# nano /etc/inittab
2:2345:respawn:/sbin/mgetty -n 3 /dev/ttyACM0

```

```

root@wani:~# nano /etc/mgetty+sendfax/mgetty.config

#
# mgetty configuration file
#
# this is a sample configuration file, see mgetty.info for details
#
# comment lines start with a "#", empty lines are ignored


# ----- global section -----
#
# In this section, you put the global defaults, per-port stuff is below


# set the global debug level to "4" (default from policy.h)
debug 4

# set the local fax station id
fax-id  

# access the modem(s) with 38400 bps
speed 38400

# use an alternate issue file, to avoid being bitten by linuxlogo
issue-file /etc/issue.mgetty

#  use these options to make the /dev/tty-device owned by "uucp.uucp" 
#  and mode "rw-rw-r--" (0664). *LEADING ZERO NEEDED!*
#port-owner uucp
#port-group uucp
#port-mode 0664

#  use these options to make incoming faxes owned by "root.uucp" 
#  and mode "rw-r-----" (0640). *LEADING ZERO NEEDED!*
#fax-owner root
#fax-group uucp
#fax-mode 0640


# ----- port specific section -----
# 
# Here you can put things that are valid only for one line, not the others
#

# Zoom V.FX 28.8, connected to ttyS0: don't do fax, less logging
#
#port ttyS0
#  debug 3
#  data-only y

# some other Rockwell modem, needs "switchbd 19200" to receive faxes
# properly (otherwise it will fail with "timeout").
#
#port ttyS1
#  speed 38400
#  switchbd 19200

# ZyXEL 2864, connected to ttyS2: maximum debugging, grab statistics
#
#port ttyS2
#  debug 8
#  init-chat "" \d\d\d+++\d\d\dAT&FS2=255 OK ATN3S0=0S13.2=1 OK 
#  statistics-chat "" AT OK ATI2 OK
#  statistics-file /var/log/statistics.ttyS2
#  modem-type cls2

# direct connection of a VT100 terminal which doesn't like DTR drops
# ("direct" meaning "*no* *modem*".  NEVER enable "direct yes" on modem lines!)
#
#port ttyS3
#  direct y
#  speed 19200
#  toggle-dtr n

```

```

root@wani:~# nano /etc/mgetty+sendfax/login.config

# login.config
#
# This is a sample "login dispatcher" configuration file for mgetty
#
# Format:
#	username userid utmp_entry login_program [arguments]
#
# Meaning:
#       for a "username" entered at mgettys login: prompt, call
#	"login_program" with [arguments], with the uid set to "userid",
#	and a USER_PROCESS utmp entry with ut_user = "utmp_entry"
#
# username may be prefixed / suffixed by "*" (wildcard)
#
# userid is a valid user name from /etc/passwd, or "-" to not set
#  a login user id and keep the uid/euid root (needed for /bin/login)
#
# utmp_entry is what will appear in the "who" listing. Use "-" to not
#  set an utmp entry (a must for /bin/login), use "@" to set it to the
#  username entered. Maximum length is 8 characters.
#
# login_program is the program that will be exec()ed, with the arguments
#  passed in [arguments]. A "@" in the arguments will be replaced with the
#  username entered. Warning: if no "@" is given, the login_program has
#  no way to know what user name the user entered.
#
#
# SAMPLES:
# Use this one with my Taylor-UUCP and Taylor-UUCP passwd files. 
#  (Big advantage: tuucp can use the same passwd file for serial dial-in 
#   and tcp dial-in [uucico running as in.uucpd]). Works from 1.05 up.
#
#U*	uucp	@	/usr/sbin/uucico -l -u @

#
# Use this one for fido calls (login name /FIDO/ is handled specially)
#
# You need Eugene Crosser's "ifmail" package for this to work.
#  mgetty has to be compiled with "-DFIDO", otherwise a fido call won't
#  be detected.
#
#/FIDO/	uucp	fido	/usr/lib/fnet/ifcico @

#
# Automatic PPP startup on receipt of LCP configure request (AutoPPP).
#  mgetty has to be compiled with "-DAUTO_PPP" for this to work.
#  Warning: Case is significant, AUTOPPP or autoppp won't work!
#  Consult the "pppd" man page to find pppd options that work for you.
#
#  NOTE: for *some* users, the "-detach" option has been necessary, for 
#        others, not at all. If your pppd doesn't die after hangup, try it.
#
#  NOTE2: "debug" creates lots of debugging info.  LOOK AT IT if things
#         do not work out of the box, most likely it's a ppp problem!
#
#  NOTE3: "man pppd" is your friend!
#
#  NOTE4: max. 9 arguments allowed.
#
/AutoPPP/ -	a_ppp	/usr/sbin/pppd auth -chap +pap login debug

#
#
# An example where no login name in the argument list is desired:
#  automatically telnetting to machine "smarty" for a given login name
#
#telnet-smarty	gast	telnet	/usr/bin/telnet -8 smarty
#
# This is the "standard" behaviour - *dont* set a userid or utmp
#  entry here, otherwise /bin/login will fail!
#  This entry isn't really necessary: if it's missing, the built-in
#  default will do exactly this.
#
*	-	-	/bin/login @

```

```

root@wani:~# nano /etc/mgetty+sendfax/dialin.config

# dialin.config (CNDFILE in policy.h)
#
# cndfile contains a series of tokens separated by newlines, commas, tabs
# and spaces.  The callerid number is compared with each token in turn,
# until a match occurs.  A match occurs when the token compares equally to
# the callerid information up to the length of the token.  If the token is
# prefixed with a "!", a match means "do not answer the phone".  The token
# "all" matches any telephone number, and will terminate scanning of the
# cndfile.  If no callerid number is present, it is assumed to have the
# value "none".  A line starting with "#" is a comment.  There is an
# implicit "all" at the end of the file.
# 
# For example:

# list of my friends' data lines
#3433535, 7445343, 5551212
#
# dad's fax
#4164646777
#
# disallow [other] calls from numbers matching the following prefix:
#!416
#
# disallow that speed dialer that keeps hitting my machine
#!3444444
#
# allow all calls with the following prefixes
#832, 555
#
# don't allow calls when there's no callerid:
#!none
#
# It's okay to accept calls from out of area
# ("OUT_OF_AREA" token seems ZyXEL specific)
#OUT_OF_AREA
# For V.253 compatibles modems "OUT OF AREA" is represented by the
# single letter 'O'
#O
#
# The caller has denied the transmission of his number
# (private service) (For German Telecom dialprefix *31#).
# This is for V.253 compatible modems represented by the single
# letter 'P'.
# don't allow access to my machine for those callers
#!P
# 
#
# disallow all other calls
#!all

```

Please help

---

### Post by dalitso on 2010-09-25
This is how I solved it

1) Pasted the following into /etc/init/ttyS0.conf 
# ttyS0 - mgetty
#
# This service maintains a mgetty on ttyS0 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/mgetty -n 2 ttyS0

2) Ask upstart to start the mgetty 
sudo start ttyS0


I got the idea from here [https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

---

