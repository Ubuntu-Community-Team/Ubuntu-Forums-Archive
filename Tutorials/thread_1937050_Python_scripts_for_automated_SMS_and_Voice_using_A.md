---
title: "Python scripts for automated SMS and Voice using AT commands"
date: 2012-03-07
forum: Tutorials
---

### Post by matogrosso on 2012-03-07
Python scripts for automated SMS and Voice using AT commands

############## AS POSTED on INTRANET WIKI #####################################
Working from home and want to use a handset in the office? Or maybe you are in the office but feeling too lazy to type numbers and letters in a tiny handset keyboard.

The scripts aforementioned use AT commands and were tested on Nokia 6700. Should work on most Nokias and Sony Ericsson running Symbian. Do not work on Android or Iphone as they do not support AT commands.

Feel free to log into my linux machine:

cd into /root/pyscripts/

And find these four scripts: at_cmds.py, send_sms.py, voice_call.py and end_call.py

1 - Connect a Nokia handset to my linux box (on my desk) using a USB cable

2 - On the Nokia handset select "PC suite"

3 - On my linux machine (192.168.21.9) under /root/pyscripts/

**To make a voice call to number 384005 type:**

[root@Oscareth1 pyscripts]# python voice_call.py 384005

**To end a voice call type:**
[root@Oscareth1 pyscripts]# python end_call.py

**To send a text message (e.g. "This is the message") to number 384005 type:**

[root@Oscareth1 pyscripts]# python send_sms.py 384005 This is the message

Alternatively, if you prefer to do this from any other linux box just copy the scripts attached to the linux box and install the following packages:

# sudo apt-get install python-setuptools

# easy_install pyserial

AUTOMATICALLY ANSWER THE VOICE CALL by using an android phone as the dialled subscriber:

1 - Goto to Android Market -> Donwload and install the free application "Lazy Car"

2 - Set Lazy Car to answer all calls. Automatic SMS reply is also supported

All python scripts mentioned are posted below



###########################
File: at_cmds.py
###########################

#!/usr/bin/env python
"""
at_cmds_v4.py - All AT commands and all classes are here. Call them from outside.
"""
## The packges below must be installed in advance
## sudo apt-get install python-setuptools
## easy_install pyserial

import serial
import time

class ATcommands:
def setDialledNumber(self, number):
self.dialledNumber = number

def setRecipient(self, number):
self.recipient = number

def setContent(self, message):
self.content = message

def connectPhone(self):
self.ser = serial.Serial('/dev/ttyACM0', 460800, timeout=5)
time.sleep(1)

def disconnectPhone(self):
self.ser.close()


class TextMessage:
def __init__(self, recipient="0000000", message="TextMessage.content not set."):
self.recipient = recipient
self.content = message

def sendMessage(self):
self.ser = serial.Serial('/dev/ttyACM0', 460800, timeout=5)
self.ser.write('ATZ\r')
time.sleep(1)
self.ser.write('AT+CMGF=1\r')
time.sleep(1)
self.ser.write('''AT+CMGS="''' + self.recipient + '''"\r''')
time.sleep(1)
self.ser.write(self.content + "\r")
time.sleep(1)
self.ser.write(chr(26))
time.sleep(1)


class VoiceCall:
def __init__(self, dialledNumber='000000'):
self.dialledNumber = dialledNumber

def dialNumber(self):
self.ser = serial.Serial('/dev/ttyACM0', 460800, timeout=5)
self.ser.write('ATZ\r')
## ATZ : Restore profile ##
time.sleep(1)
self.ser.write('ATD ' + self.dialledNumber + ';\r')
## ATD : Dial command ##
## semicolon : voice call ##
time.sleep(1)
time.sleep(1)
self.ser.write(chr(26))
time.sleep(1)
time.sleep(1)
time.sleep(1)

def endCall(self):
self.ser = serial.Serial('/dev/ttyACM0', 460800, timeout=5)
self.ser.write('ATZ\r')
time.sleep(1)
self.ser.write('AT+CHUP\r')
time.sleep(1)
self.ser.write(chr(26))
time.sleep(1)




#Main function that calls other functions - Makes script reusable
def main():
pass

if __name__ == "__main__":
main()




###########################
###########################
File: send_sms.py
###########################
#!/usr/bin/env python
# -*- coding: iso-8859-15 -*-
"""
Use this to call the sms function
It is for sending SMS using AT commands - version v3
"""
## The packges below must be installed in advance
## sudo apt-get install python-setuptools
## easy_install pyserial

import serial
import time
import sys

from at_cmds import ATcommands
from at_cmds import TextMessage

if len(sys.argv) > 1:
phoneNumber = sys.argv[1]
message = ""
if len(sys.argv) >= 2:
for i in range(2, len(sys.argv)):
message = message + " " + sys.argv[i]

message = message.strip()
print "number = " + phoneNumber + ", message = " + message
sms = TextMessage(phoneNumber, message)
else:
sms = TextMessage()

usb_serial = ATcommands()

usb_serial.connectPhone()
sms.sendMessage()
usb_serial.disconnectPhone()

#Main function that calls other functions - Makes script reusable
def main():
pass

if __name__ == "__main__":
main()




###########################
###########################
File: voice_call.py
###########################
#!/usr/bin/env python
# -*- coding: iso-8859-15 -*-
"""
Voice call using AT commands
Calls the at_cmds class definitions - version v3
"""
## The packges below must be installed in advance
## sudo apt-get install python-setuptools
## easy_install pyserial

import serial
import time
import sys
from at_cmds import ATcommands
from at_cmds import VoiceCall


if len(sys.argv) > 1:
phoneNumber = sys.argv[1]
callPhone = VoiceCall(phoneNumber)
else:
callPhone = VoiceCall()

usb_serial = ATcommands()

usb_serial.connectPhone()
callPhone.dialNumber()
usb_serial.disconnectPhone()

#Main function that calls other functions - Makes script reusable
def main():
pass

if __name__ == "__main__":
main()



###########################
###########################
File: end_call.py
###########################
#!/usr/bin/env python
# -*- coding: iso-8859-15 -*-
"""
Terminate voice call using AT commands
Calls the at_cmds class definitions - version v4
"""
## The packges below must be installed in advance
## sudo apt-get install python-setuptools
## easy_install pyserial

import serial
import time
import sys
from at_cmds import ATcommands
from at_cmds import VoiceCall

currentCall = VoiceCall()
usb_serial = ATcommands()

usb_serial.connectPhone()
currentCall.endCall()
usb_serial.disconnectPhone()

#Main function that calls other functions - Makes script reusable
def main():
pass

if __name__ == "__main__":
main()

---

### Post by kashif12 on 2012-04-23
Hi Matogrosso
Thanks for the scripts.
Will it be possible for you to attach them?
as doing copy paste from here caused indentation problems.

I tried to resolve indentation problems in send_sms.py
but now i am getting following


root@kashif-pc:~/pyscripts [1] 
# python send_sms.py 384005 This is the message
Traceback (most recent call last):
  File "send_sms.py", line 19, in <module>
    from at_cmds import ATcommands
  File "/root/pyscripts/at_cmds.py", line 17
    def setDialledNumber(self, number):
      ^

---

### Post by meeth on 2013-02-21
Hi , thanks for sharing the code. Can you please provide a script to read sms from a modem( or  nokia phone )

---

