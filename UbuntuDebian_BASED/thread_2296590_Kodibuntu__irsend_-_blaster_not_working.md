---
title: "Kodibuntu:  irsend - blaster not working"
date: 2015-09-27
forum: Ubuntu/Debian BASED
---

### Post by scsmolaga on 2015-09-27
Hello, so I have searched the net but can't get my blaster working using irsend,

I have an HP USB IR transiever which I am using to control Kodi in Kodibuntu. 
Receiving works fine, but I am trying to send a power toggle signal to a sony hifi system via a blaster cable.

I have added the command to etc/lirc/lircd.conf.mceusb using irrecord. Then using irw the command is recognised when using the hifi's remote and a harmony 650 with the button programmed in.
However using      irsend SEND_START sony KEY_PROG1      nothing happens - as in no errors or anything in the terminal.
 Any suggestions?

Also In Windows I have done this using evenghost so I know the hardware itself is capable incase that's relevant!

 Below are my conf files for lirc:

etc/lirc/hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""


#Chosen IR Transmitter
TRANSMITTER=""
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf.mceusb"
TRANSMITTER_LIRCD_ARGS=""


#Enable lircd
START_LIRCD="true"


#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"


#Try to load appropriate kernel modules
LOAD_MODULES="true"


# Default configuration files for your hardware if any
LIRCMD_CONF=""


#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""

```

etc/lirc/lircd.conf:
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.


#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"



```
etc/lirc/lircd.conf.mceusb:
```
#
# brand:                        HP/Philips/Microsoft/Other
# model no. of remote control:  Media Center Edition remote
# devices being controlled by this remote: HP Slimline S3100y and a
# myriad of devices with Media Center Edition receivers
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects_remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#
#
# Updated with codes for MCE 2007 Remote additional buttons
# Visualization, Aspect, SlideShow, Eject
# Note: 
# Renamed some buttons: DVD->DVDMenu, More->MoreInfo, Star->Asterisk, Hash->Pound
# Note: 
# Blue, Yellow, Green, Red, and Teletext buttons do not exist on the HP remote


begin remote


  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100


  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
  toggle_bit           22
  rc6_mask    0x100000000




      begin codes


#seen on HP Pavilion dv3t remote  --Tim Mann, 3 Nov 2009
    Media         0x00007b7f
    PlayPause     0x00007b91




#unused by HP remote
    KEY_BLUE          0x00007ba1
    KEY_YELLOW          0x00007ba2
    KEY_GREEN          0x00007ba3
    KEY_RED          0x00007ba4
    Teletext      0x00007ba5


#ba6 - bae unused 
        BA6           0x00007ba6
        BA7           0x00007ba7
        BA8           0x00007ba8
        BA9           0x00007ba9
        BAA           0x00007baa
        BAB           0x00007bab
        BAC           0x00007bac
        BAD           0x00007bad
        BAE           0x00007bae


        KEY_RADIO         0x00007baf
        Print         0x00007bb1


#bb2 - bb4 unused  
        BB2           0x00007bb2
        BB3           0x00007bb3
        BB4           0x00007bb4


        KEY_VIDEO        0x00007bb5
        Pictures      0x00007bb6
        RecTV         0x00007bb7
        KEY_AUDIO         0x00007bb8
        KEY_TV            0x00007bb9


#bba - bbf unused 
        BBA           0x00007bba
        BBB           0x00007bbb
        BBC           0x00007bbc
        BBD           0x00007bbd
        BBE           0x00007bbe
        BBF           0x00007bbf
#bc1 - bca unused 
        BC1           0x00007bc1
        BC2           0x00007bc2
        BC3           0x00007bc3
        BC4           0x00007bc4
        BC5           0x00007bc5
        BC6           0x00007bc6
        BC7           0x00007bc7
        BC8           0x00007bc8
        BC9           0x00007bc9
        BCA           0x00007bca


        KEY_EJECTCD         0x00007bcb
        SlideShow     0x00007bcc
        Visualization 0x00007bcd


#bce - bcf unused 
        BCE           0x00007bce
        BCF           0x00007bcf
#bd1 - bd7 unused 
        BD1           0x00007bd1
        BD2           0x00007bd2
        BD3           0x00007bd3
        BD4           0x00007bd4
        BD5           0x00007bd5
        BD6           0x00007bd6
        BD7           0x00007bd7


        Aspect        0x00007bd8
        Guide         0x00007bd9
        LiveTV        0x00007bda
        KEY_DVD           0x00007bdb
#NoGap
        KEY_BACK          0x00007bdc
        KEY_OK            0x00007bdd
        KEY_RIGHT         0x00007bde
        KEY_LEFT          0x00007bdf
        KEY_DOWN          0x00007be0
        KEY_UP            0x00007be1
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        KEY_AGAIN        0x00007be4
        KEY_NEXT          0x00007be5
        KEY_STOP          0x00007be6
        KEY_PAUSE         0x00007be7
        KEY_RECORD        0x00007be8
        KEY_PLAY          0x00007be9
        KEY_REWIND        0x00007bea
        KEY_FORWARD       0x00007beb
#NoGap
        KEY_CHANNELDOWN      0x00007bec
        KEY_CHANNELUP        0x00007bed
        KEY_VOLUMEDOWN       0x00007bee
        KEY_VOLUMEUP         0x00007bef
#NoGap
        More          0x00007bf0
        KEY_MUTE          0x00007bf1
        KEY_HOME          0x00007bf2
        KEY_POWER         0x00007bf3
#NoGap
        KEY_ENTER         0x00007bf4
        KEY_CLEAR         0x00007bf5
#NoGap
        KEY_9          0x00007bf6
        KEY_8         0x00007bf7
        KEY_7         0x00007bf8
        KEY_6           0x00007bf9
        KEY_5          0x00007bfa
        KEY_4          0x00007bfb
        KEY_3         0x00007bfc
        KEY_2           0x00007bfd
        KEY_1           0x00007bfe
        KEY_0          0x00007bff
      end codes


end remote
#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Mon Feb 23 23:55:04 2009
#
# contributed by 
#
# brand:                       Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR-150 Remote (MCE kit)
# SMK dongle 0609:031d
#


begin remote


  name  mceusb_hauppauge
  bits           13
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100


  header       2674   870
  one           455   427
  zero          455   427
  pre_data_bits   24
  pre_data       0x1BFF82
  gap          106288
  min_repeat      1
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000


      begin codes
          TV                       0x1BB9
          Music                    0x1BB8
          Pictures                 0x1BB6
          Videos                   0x1BB5
          Power                    0x1BF3
          Stop                     0x1BE6
          Record                   0x1BE8
          Pause                    0x1BE7
          Play                     0x1BE9
          Rewind                   0x1BEA
          Foward                   0x1BEB
          Replay                   0x1BE4
          Skip                     0x1BE5
          Back                     0x1BDC
          More                     0x1BF0
          Up                       0x1BE1
          Left                     0x1BDF
          Right                    0x1BDE
          OK                       0x1BDD
          Down                     0x1BE0
          VolUp                    0x1BEF
          VolDown                  0x1BEE
          Home                     0x1BF2
          ChanDown                 0x1BED
          ChanUp                   0x1BEC
          Mute                     0x1BF1
          RecTV                    0x1BB7
          Guide                    0x1BD9
          LiveTV                   0x1BDA
          DVD                      0x1BDB
          One                      0x1BFE
          Two                      0x1BFD
          Three                    0x1BFC
          Four                     0x1BFB
          Five                     0x1BFA
          Six                      0x1BF9
          Seven                    0x1BF8
          Eight                    0x1BF7
          Nine                     0x1BF6
          Star                     0x1BE2
          Zero                     0x1BFF
          Hash                     0x1BE3
          Clear                    0x1BF5
          Enter                    0x1BF4
      end codes


end remote




#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Tue Mar 10 19:27:09 2009
#
# contributed by 
#
# brand:  SIIG Vista MCE remote
# model no. of remote control: 
# devices being controlled by this remote:
#


begin remote


  name  vista_mce
  bits           16
  flags RC6
  eps            30
  aeps          100


  header       2654   889
  one           427   427
  zero          427   427
  pre_data_bits   21
  pre_data       0x37FF0
  gap          69850
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000


      begin codes
          Power                    0xEBF3
          Pictures                 0x6BB6
          Radio                    0xEBAF
          Videos                   0x6BB5
          Music                    0xEBB8
          Rec                      0x6BE8
          Pause                    0xEBE7
          Stop                     0x6BE6
          Skipback                 0xEBE4
          Play                     0x6BE9
          Skipfwd                  0xEBE5
          Rwd                      0x6BEA
          Fwd                      0xEBEB
          Start                    0x6BF2
          Back                     0xEBDC
          More                     0x6BF0
          Volup                    0xEBEF
          Voldown                  0x6BEE
          Chup                     0xEBED
          Chdown                   0x6BEC
          Up                       0xEBE1
          Down                     0x6BE0
          Left                     0xEBDF
          Right                    0x6BDE
          Mute                     0xEBF1
          Rectv                    0x6BB7
          Guide                    0xEBD9
          Livetv                   0x6BDA
          Dvdmenu                  0xEBDB
          1                        0x6BFE
          2                        0xEBFD
          3                        0x6BFC
          4                        0xEBFB
          5                        0x6BFA
          6                        0xEBF9
          7                        0x6BF8
          8                        0xEBF7
          9                        0x6BF6
          *                        0xEBE2
          0                        0x6BFF
          #                        0xEBE3
          Clear                    0x6BF5
          Enter                    0xEBF4
      end codes


end remote


begin remote


  name  sony
  bits           20
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100


  header       2370   659
  one          1138   664
  zero          538   664
  gap          45151
  min_repeat      2
#  suppress_repeat 2
#  uncomment to suppress unwanted repeats
  toggle_bit_mask 0x0


      begin codes
          KEY_PROG1                0xA8281
      end codes


end remote



```

---

### Post by QIII on 2015-09-27
*Moved to **Ubuntu/Debian BASED***

Kodibuntu, like its predecessor XBMCbuntu, is not an officially recognized flavor of Ubuntu.

---

