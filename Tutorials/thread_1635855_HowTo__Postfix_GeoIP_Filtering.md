---
title: "HowTo : Postfix GeoIP Filtering"
date: 2010-12-02
forum: Tutorials
---

### Post by Malac on 2010-12-02
Hi,
I've been looking for a way to filter out emails on my postfix server by GeoIP data.
I couldn't find anything that fitted the bill so wrote my own in Python as a postfix policy.
Thought I'd post it here to see if it's of any use to anyone else.
I've attached a tar of the files as the Python formatting will get mucked up by the forum code.
 
Comments/improvements are welcome (be kind :) )
 
First file is : policyd-geoip which is owned by root:root and placed in /usr/bin with 755 perms
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#
# Check GeoIP country_codes and provide recommended action back to Postfix.
#
# policyd-geoip
# Copyright 2010 Malac <[EMAIL="malacusp@gmail.com"]malacusp@gmail.com[/EMAIL]>
'''
This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License version 2 as published 
by the Free Software Foundation.
This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.
You should have received a copy of the GNU General Public License along
with this program; if not, write to the Free Software Foundation, Inc.,
51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.'''
__version__ = "1.00: DEC 09, 2010"
import syslog, sys, os, string #, time, atexit
import GeoIP
import re
# Function to Query IP against GeoIP database
def query(data, instance_dict, path_to_data):
IP = data.get('client_address')
if IP == None:
syslog.syslog('geoip/query: No client address, exiting')
return(( None, instance_dict ))
instance = data.get('instance')
# The following if is only needed for testing. Postfix 
# will always provide instance.
if not instance:
import random
instance = str(int(random.random()*100000))
# This is to prevent multiple headers being prepended
# for multi-recipient mail.
if instance_dict.has_key(instance):
found_instance = instance_dict[instance]
else:
found_instance = []
# If this is not the first recipient for the message, we need to know if
# there is a previous prepend to make sure we don't prepend more than once.
if found_instance:
if found_instance[6] != 'prepend':
last_action = found_instance[3]
else:
last_action = found_instance[6]
else:
# This is the actual query "gi" is defined later in the code.
retval=gi.country_code_by_addr(IP)
return(( retval, instance_dict ))
return(( 'None', instance_dict ))
# Function to check for exceptions to the BADLIST so they can be passed even if their country is unacceptable
def check_bad_exceptions(data, saved_result, bad_exceptions, IP, revlookup):
if passed == "-D":
syslog.syslog('exceptions_to_badlist: %s' % (bad_exceptions))
syslog.syslog('IP: %s' % (IP))
syslog.syslog('Reverse DNS Lookup: %s' % (revlookup))
# If "BADEXCEPT" or "GOODEXCEPT" or "SENDEREXCEPT" already then just return that
if (saved_result == "GOODEXCEPT" or saved_result == "SENDEREXCEPT" or saved_result == "RECIPIENTEXCEPT"):
return ( saved_result )
# Check each entry in bad_exceptions against the IP then the revlookup
for server in bad_exceptions:
if (server in IP) and (server != ''):
return ( "BADEXCEPT" )
if (server in revlookup.upper()) and (server != ''):
return ( "BADEXCEPT" )
return ( saved_result )
# Function to check for exceptions to the GOODLIST so they can be rejected even if their country is acceptable
def check_good_exceptions(data, saved_result, good_exceptions, IP, revlookup):
if passed == "-D":
syslog.syslog('exceptions_to_goodlist: %s' % (good_exceptions))
syslog.syslog('IP: %s' % (IP))
syslog.syslog('Reverse DNS Lookup: %s' % (revlookup))
# If "BADEXCEPT" or "GOODEXCEPT" or "SENDEREXCEPT" already then just return that
if (saved_result == "BADEXCEPT" or saved_result == "SENDEREXCEPT" or saved_result == "RECIPIENTEXCEPT"):
return ( saved_result )
# Check each entry in good_exceptions against the IP then the revlookup
for server in good_exceptions:
if (server in IP) and (server != ''):
return ( "GOODEXCEPT" )
if (server in revlookup.upper()) and (server != ''):
return ( "GOODEXCEPT" )
return ( saved_result )
# Function to check for sender_exceptions so checking is bypassed
def check_sender_exceptions(data, saved_result, sender_exceptions, sender_address):
if passed == "-D":
syslog.syslog('sender_exceptions: %s' % (sender_exceptions))
syslog.syslog('Sender Address: %s' % (sender_address))
# If "BADEXCEPT" or "GOODEXCEPT" or "SENDEREXCEPT" already then just return that
if (saved_result == "BADEXCEPT" or saved_result == "GOODEXCEPT" or saved_result == "RECIPIENTEXCEPT"):
return ( saved_result )
# Check each entry in sender_exceptions against the IP then the revlookup
for address in sender_exceptions:
if (address in sender_address.upper()) and (address != ''):
return ( "SENDEREXCEPT" )
return ( saved_result )
# Function to check for recipient exceptions so checking is bypassed
def check_recipient_exceptions(data, saved_result, recipient_exceptions, recipient_address):
if passed == "-D":
syslog.syslog('recipient_exceptions: %s' % (recipient_exceptions))
syslog.syslog('Recipient Address: %s' % (recipient_address))
# If "BADEXCEPT" or "GOODEXCEPT" or "SENDEREXCEPT" already then just return that
if (saved_result == "BADEXCEPT" or saved_result == "GOODEXCEPT" or saved_result == "SENDEREXCEPT"):
return ( saved_result )
# Check each entry in sender_exceptions against the IP then the revlookup
for address in recipient_exceptions:
if (address in recipient_address.upper()) and (address != ''):
return ( "RECIPIENTEXCEPT" )
return ( saved_result )
################
# MAIN PROGRAM #
################
# Load Mail Log for output messages
passed = ""
debugmode = ""
if len(sys.argv) >= 2:
#debug stuff
passed = sys.argv[1]
passed = passed.upper()
if passed == "-D":
debugmode = "in Debug Mode"
syslog.openlog(os.path.basename(sys.argv[0]), syslog.LOG_PID, syslog.LOG_MAIL)
syslog.syslog('Running GeoIP Policy Check %s' % (debugmode))
# Load and Read config file
conf_file = open( '/etc/postfix-policyd-geoip/policyd-geoip.conf', 'r')
config = conf_file.readlines()
conf_file.close()
# Setup some variables
whitespace = re.compile(r'\s+')
path_to_data = "/usr/share/GeoIP/GeoIP.dat"
badlist=[]
goodlist=[]
bad_exceptions=[]
good_exceptions=[]
sender_exceptions=[]
recipient_exceptions=[]
permit_goodlist_only=False
soft_bounce=False
test_mode=False
reject_code="450"
PGO_message=""
# Now Read through the config array and assign values
for i in range( len( config ) ):
data_file=config[i] # needs to be saved as normal case as other values are uppercased later.
value = whitespace.sub('',config[i])
value = value.upper()
value = value.split('=')
if value[0][0:12] == "PATH_TO_DATA":
codes = data_file.strip('\n')
codes = codes.strip('\r')
data_file = codes.split('=')
try:
path_to_data = data_file[1].strip(' ')
except:
path_to_data = "/usr/share/GeoIP/GeoIP.dat"
pass
elif value[0][0:7] == "BADLIST":
codes = value[1].strip('\n')
codes = codes.strip('\r')
badlist = codes.split(',')
elif value[0][0:8] == "GOODLIST":
codes = value[1].strip('\n')
codes = codes.strip('\r')
goodlist = codes.split(',')
elif value[0][0:21] == "EXCEPTIONS_TO_BADLIST":
codes = value[1].strip('\n')
codes = codes.strip('\r')
codes = codes.strip('*')
bad_exceptions = codes.split(',')
elif value[0][0:22] == "EXCEPTIONS_TO_GOODLIST":
codes = value[1].strip('\n')
codes = codes.strip('\r')
codes = codes.strip('*')
good_exceptions = codes.split(',')
elif value[0][0:17] == "SENDER_EXCEPTIONS":
codes = value[1].strip('\n')
codes = codes.strip('\r')
codes = codes.strip('*')
sender_exceptions = codes.split(',')
elif value[0][0:20] == "RECIPIENT_EXCEPTIONS":
codes = value[1].strip('\n')
codes = codes.strip('\r')
codes = codes.strip('*')
recipient_exceptions = codes.split(',')
elif value[0][0:20] == "PERMIT_GOODLIST_ONLY":
codes = value[1].strip('\n')
codes = codes.strip('\r')
if codes == "TRUE" or codes == "1" or codes == "on":
permit_goodlist_only = True
else:
permit_goodlist_only = False
elif value[0][0:11] == "SOFT_BOUNCE":
codes = value[1].strip('\n')
codes = codes.strip('\r')
if codes == "TRUE" or codes == "1" or codes == "on":
soft_bounce = True
else:
soft_bounce = False
elif value[0][0:9] == "TEST_MODE":
codes = value[1].strip('\n')
codes = codes.strip('\r')
if codes == "TRUE" or codes == "1" or codes == "on":
test_mode = True
else:
test_mode = False
# Set Reject Code '450' soft bounce temporarily unavailable, '550' permanently unavailable.
if (soft_bounce):
reject_code = '450'
else:
reject_code = '550'
if permit_goodlist_only:
PGO_message = "permit_goodlist_only is TRUE"
if passed == "-D":
syslog.syslog('reject_code set to: %s' % (reject_code))
syslog.syslog('permit_goodlist_only is: %s' % (permit_goodlist_only))
syslog.syslog('test_mode set to: %s' % (test_mode))
 
# Open the GeoIP database.
gi = GeoIP.open(path_to_data, GeoIP.GEOIP_STANDARD)
instance_dict = {'0':'init',}
instance_dict.clear()
data = {}
lineRx = re.compile(r'^\s*([^=\s]+)\s*=(.*)$')
while 1:
line = sys.stdin.readline()
if not line: break
line = string.rstrip(line)
if not line:
try:
# Perform Check of IP
result, instance_dict = query(data, instance_dict, path_to_data)
# Save country_code for later use.
saved_result = result
IP = data.get('client_address')
sender_address = data.get('sender')
recipient_address = data.get('recipient')
revlookup = data.get('reverse_client_name')
syslog.syslog( 'E-Mail Sender <%s> to Recipient <%s>' % (sender_address, recipient_address) )
if passed == "-D":
syslog.syslog('Postfix Reverse Lookup of %s returned %s' % (IP, revlookup) )
# Check for Exceptions
result = check_good_exceptions(data, result, good_exceptions, IP, revlookup)
result = check_bad_exceptions(data, result, bad_exceptions, IP, revlookup)
result = check_sender_exceptions(data, result, sender_exceptions, sender_address )
result = check_recipient_exceptions(data, result, recipient_exceptions, recipient_address )
if passed == "-D":
syslog.syslog('Result of Checks: %s' % (result))
# Check result - "action=dunno" is used instead of "action=ok" as this lets other checks happen.
if (result == "SENDEREXCEPT"):
if test_mode:
sys.stdout.write( 'action=dunno TEST_MODE\n\n' )
syslog.syslog( '[TEST_MODE active, result would be] action=Pass - No Processing <%s> in SENDER_EXCEPTIONS %s' % (sender_address, PGO_message) )
else:
sys.stdout.write( 'action=dunno No Processing <%s> in SENDER_EXCEPTIONS\n\n' % (sender_address) )
syslog.syslog( 'action=Pass - No Processing <%s> in SENDER_EXCEPTIONS ' % (sender_address) )
elif (result == "RECIPIENTEXCEPT"):
if test_mode:
sys.stdout.write( 'action=dunno TEST_MODE\n\n' )
syslog.syslog( '[TEST_MODE active, result would be] action=Pass - No Processing <%s> in RECIPIENT_EXCEPTIONS %s' % (recipient_address,PGO_message) )
else:
sys.stdout.write( 'action=dunno No Processing <%s> in RECIPIENT_EXCEPTIONS\n\n' % (recipient_address) )
syslog.syslog( 'action=Pass - No Processing <%s> in RECIPIENT_EXCEPTIONS ' % (recipient_address) )
elif (result == "BADEXCEPT"):
if test_mode:
sys.stdout.write( 'action=dunno TEST_MODE\n\n' )
syslog.syslog( '[TEST_MODE active, result would be] action=Pass - Accepted Server [IP: %s / LOOKUP: %s] in EXCEPTIONS_TO_BADLIST returns :- %s %s' % (IP,revlookup,saved_result,PGO_message) )
else:
sys.stdout.write( 'action=dunno Accepted Server [IP: %s / LOOKUP: %s] in EXCEPTIONS returns :- %s\n\n' % (IP,revlookup,saved_result) )
syslog.syslog( 'action=Pass - Accepted Server [IP: %s / LOOKUP: %s] in EXCEPTIONS_TO_BADLIST returns :- %s ' % (IP,revlookup,saved_result) )
elif (result == "GOODEXCEPT"):
if test_mode:
sys.stdout.write( 'action=dunno TEST_MODE\n\n' )
syslog.syslog( '[TEST_MODE active, result would be] action=%s - Rejected Server [IP:%s / LOOKUP:%s] in EXCEPTIONS_TO_GOODLIST returns :- %s %s' % (reject_code,IP,revlookup,saved_result,PGO_message) )
else:
sys.stdout.write( 'action=%s Rejected Server [IP: %s / LOOKUP: %s] in EXCEPTIONS returns :- %s\n\n' % (reject_code,IP,revlookup,saved_result) )
syslog.syslog( 'action=%s - Rejected Server [IP:%s / LOOKUP:%s] in EXCEPTIONS_TO_GOODLIST returns :- %s ' % (reject_code,IP,revlookup,saved_result) )
elif (result in badlist):
if test_mode:
sys.stdout.write( 'action=dunno TEST_MODE\n\n' )
syslog.syslog( '[TEST_MODE active, result would be] action=%s - Rejected Server [IP: %s / LOOKUP: %s] in BADLIST as %s %s' % (reject_code,IP,revlookup,saved_result,PGO_message) )
else:
sys.stdout.write( 'action=%s Rejected Server [IP: %s / LOOKUP: %s] in BADLIST as %s\n\n' % (reject_code,IP,revlookup,saved_result) )
syslog.syslog( 'action=%s - Rejected Server [IP: %s / LOOKUP: %s] in BADLIST as %s ' % (reject_code,IP,revlookup,saved_result) )
elif (result in goodlist):
if test_mode:
sys.stdout.write( 'action=dunno TEST_MODE\n\n' )
syslog.syslog( '[TEST_MODE active, result would be] action=Pass - Accepted Server [IP: %s / LOOKUP: %s] in GOODLIST as %s %s' % (IP,revlookup,result,PGO_message) )
else:
sys.stdout.write( 'action=dunno Accepted Server [IP: %s / LOOKUP: %s] in GOODLIST as %s\n\n' % (IP,revlookup,saved_result) )
syslog.syslog( 'action=Pass - Accepted Server [IP: %s / LOOKUP: %s] in GOODLIST as %s ' % (IP,revlookup,saved_result) )
else:
if( permit_goodlist_only ):
if test_mode:
sys.stdout.write( 'action=dunno TEST_MODE\n\n' )
syslog.syslog( '[TEST_MODE active, result would be] action=%s - Rejected Server [IP: %s / LOOKUP: %s] not in GOODLIST or BADLIST returns :- %s %s' % (reject_code,IP,revlookup,saved_result,PGO_message) )
else:
sys.stdout.write( 'action=%s Rejected Server [IP: %s / LOOKUP: %s] not in GOODLIST or BADLIST returns :- %s\n\n' % (reject_code,IP,revlookup,saved_result) )
syslog.syslog( 'action=%s - Rejected Server [IP: %s / LOOKUP: %s] not in GOODLIST or BADLIST returns :- %s ' % (reject_code,IP,revlookup,saved_result) )
else:
if test_mode:
sys.stdout.write( 'action=dunno TEST_MODE\n\n' )
syslog.syslog( '[TEST_MODE active, result would be] action=warn Server [IP: %s / LOOKUP: %s] not in GOODLIST or BADLIST returns :- %s ' % (IP,revlookup,saved_result) )
else:
sys.stdout.write( 'action=warn Server [IP: %s / LOOKUP: %s] not in GOODLIST or BADLIST returns :- %s\n\n' % (IP,revlookup,saved_result) )
syslog.syslog( 'action=warn - Server [IP: %s / LOOKUP: %s] not in GOODLIST or BADLIST returns :- %s ' % (IP,revlookup,saved_result) )
except Exception, cause :
sys.stdout.write( 'action=dunno An error occured, %s failed with error %s\n\n' % (IP,str(cause)) )
syslog.syslog('An Error Occured, %s failed with error %s' % (IP, str(cause)) )
pass
sys.stdout.flush()
data = {}
continue
m = lineRx.match(line)
if not m: 
syslog.syslog('ERROR: Could not match line "%s"' % line)
continue
key = m.group(1)
value = m.group(2)
if key not in [ 'protocol_state', 'protocol_name', 'queue_id' ]:
value = string.lower(value)
data[key] = value
```
 
Second File is policyd-geoip.conf file which is owned by root:root and placed in /etc/postfix-policyd-geoip with 644 perms
```
path_to_data = /usr/share/GeoIP/GeoIP.dat
badlist = CN,CZ,NL,IT,IN,TW,VE,VN,ZA
goodlist = GB,US,CA,IE
exceptions_to_badlist = example.com, okaysite, myserver.com, 10.0.0.1,
exceptions_to_goodlist =
sender_exceptions = user@example.com
recipient_exceptions =
permit_goodlist_only = false
soft_bounce = true
test_mode=true
```**[COLOR=darkred]path_to_data[/COLOR]** is set to the location of the GeoIP database.
[COLOR=darkred]**badlist**[/COLOR] is a comma separated list of the GeoIP country_codes you want to reject.
[COLOR=darkred]**goodlist**[/COLOR] is a comma separated list of the GeoIP country_codes you want to accept if permit_goodlist_only is set to true.
[COLOR=darkred][COLOR=darkred]**exceptions_to_badlist** [/COLOR][COLOR=black]these are a comma separated list of exceptions and must be in the server revlookup entries of connections. **NOT email addresses**.[/COLOR]
[/COLOR][COLOR=darkred]**exceptions_to_goodlist **[/COLOR][COLOR=black]these [/COLOR][COLOR=black]are a comma separated list of exceptions and must be in the server revlookup entries of connections. **NOT email addresses**.[/COLOR]
[COLOR=darkred][COLOR=darkred]**sender_exceptions** [/COLOR][COLOR=black]these [/COLOR][COLOR=black]are a comma separated list of incoming email exceptions and can be in the form of single emails (user@example.com) or all (*@safestuff.example.com) or partial (example.com) no filtering is done for these senders.[/COLOR]
[COLOR=darkred]**recipient_exceptions** [/COLOR][COLOR=black]these [/COLOR][COLOR=black]are a comma separated list of your receiving email exceptions and can be in the form of single emails (user@example.com) or all (*@safestuff.example.com) or partial (example.com) no filtering is done for these recipients.[/COLOR]
[/COLOR]**[COLOR=darkred]permit_goodlist_only[/COLOR]** is to only allow country_codes on goodlist to be accepted.
**[COLOR=darkred]soft_bounce[/COLOR]** if set to true a 450 temporarily unavailable will be returned instead of a 550 permanent.
**[COLOR=darkred]test_mode[/COLOR]** if set to true no action is taken on the e-mail but an entry is placed in mail.log of what action would have been taken. This is handy for testing purposes.
 
Next we need to alter master.cf in /etc/postfix and add: 
```
policy-geoip unix - n n - 0 spawn
  user=nobody argv=/usr/bin/policyd-geoip
```You can add a -d option on the end of argv to display debug messages in the mail.log.
 
Then add the policy to end of smtpd_recipient_restrictions in main.cf like so:
```
smtpd_recipient_restrictions = permit_mynetworks,
                      permit_sasl_authenticated,
                      .........<other restrictions you have in place>........ ,
                      **check_policy_service unix:private/policy-geoip**
```Not forgetting to postmap main.cf
 
Then: sudo /etc/init.d/postfix restart and you should start seeing messages in your mail.log.
 
Thanks to the postfix-policy-spf coders for tips. 
That's it, hope this helps someone.

---

### Post by porjo on 2011-03-24
Thanks Malac for your contribution. :)

My suggestion for improvement would be to add a greylisting capability to your script so that on the first connection the IP would get a soft fail, but the second (or third or fourth...) connection from that same IP would be allowed through.

---

### Post by Malac on 2011-03-31
> **porjo said:**
> Thanks Malac for your contribution. :)
 
My suggestion for improvement would be to add a greylisting capability to your script so that on the first connection the IP would get a soft fail, but the second (or third or fourth...) connection from that same IP would be allowed through.
 
You're Welcome.
I'm still working on the project though I am trying not to put in too much functionality.
Capabilities like greylisting are already dealt with by other programs and postfix addons. Though I am looking at logging the attempts and instead of sending a 450 temporary error sending a 554 if the sending server keeps retrying within a certain time.
Thanks for the support. :)

---

### Post by porjo on 2011-04-05
"Capabilities like greylisting are already dealt with by other programs and postfix addons"


Yes, that is true. The situation I have is that I'd like to do greylisting generally but be able to classify certain countries (such as my own) as not being subject to either blacklisting or greylisting. I can see a couple of ways to achieve this, however having a single policy that does both checks in one pass seems to be the best way to handle it.

---

### Post by Ulix1 on 2011-06-12
Hello Malac,

thank you, a very good implementation for geoip-filtering.
I use it on an open-vz virtual machine, where xtables-addons cannont be compiled into iptables (no header sources are available).

My implementation is in combination with postfwd (because i want to  use it only for some domains):

main.cf:
smtpd_restriction_classes = geoip
geoip = check_policy_service unix:private/policy-geoip

postfwd.cf:
id=GEOIP1; recipient_domain=domain.tld; action=geoip


Best regards, Ulrich

---

### Post by Malac on 2011-06-17
> **Ulix1 said:**
> Hello Malac,

thank you, a very good implementation for geoip-filtering.
I use it on an open-vz virtual machine, where xtables-addons cannont be compiled into iptables (no header sources are available).

My implementation is in combination with postfwd (because i want to  use it only for some domains):

main.cf:
smtpd_restriction_classes = geoip
geoip = check_policy_service unix:private/policy-geoip

postfwd.cf:
id=GEOIP1; recipient_domain=domain.tld; action=geoip


Best regards, Ulrich
Thanks for the input Ulix1, I had not thought of using geoip with postfwd I'll take a look at that myself. Thanks for the tip.

---

### Post by anotherfakeID on 2011-10-23
I really like the promise of this policy server. However, in trying to implement it on an Ubuntu 11.04 Natty server it fails with the following log entries.

```
postfix/spawn[13670]: warning: command /usr/bin/policyd-geoip exit status 1
postfix/smtpd[13665]: warning: premature end-of-input on private/policy-geoip while reading input attribute name
postfix/smtpd[13665]: warning: problem talking to server private/policy-geoip: Connection reset by peer

```I tried enabling debug mode on policyd-geoip but, there are no further log entries than those above.

Any recommendation would be appreciated.

---

### Post by Malac on 2011-10-24
> **anotherfakeID said:**
> I really like the promise of this policy server. However, in trying to implement it on an Ubuntu 11.04 Natty server it fails with the following log entries.

```
postfix/spawn[13670]: warning: command /usr/bin/policyd-geoip exit status 1
postfix/smtpd[13665]: warning: premature end-of-input on private/policy-geoip while reading input attribute name
postfix/smtpd[13665]: warning: problem talking to server private/policy-geoip: Connection reset by peer

```I tried enabling debug mode on policyd-geoip but, there are no further log entries than those above.

Any recommendation would be appreciated.
I will start with the obvious so please forgive me if this is too basic as I don't know your level of expertise. I have this running on a Natty server myself and all is well so I would suspect a configuration error maybe.
Firstly check that you have the python modules syslog, sys, os, string, GeoIP and re
Next try running policyd-geoip from the command line, it should report where the failure actually is in the code.
I have tried to make it fail gracefully on most errors but this must be one I hadn't expected. Still I would expect a more verbose error.

If this doesn't help please try downloading the files again and checking the config files.
Also make sure your file ownership and permissions are set correctly.

If none of this helps let me know here or by pm and I'll try and get back to you asap.

---

### Post by anotherfakeID on 2011-10-25
Running the application in a terminal did indeed provide the actual reasons for failure.

In my case, a combination of a missing GeoIP Python module and my failure to properly follow the instructions(placing the conf fie in the wrong directory) were the cause. It's running well now (in test mode).

Thank you for your help and your fine policy server.


P.S. would it not be better to pass this policy first under smtpd_recipient_restrictions rather than last? It seems a waste to do all the spam and content filtering when the entire transaction should have been dumped int the first place.

---

### Post by Malac on 2011-10-28
> **anotherfakeID said:**
> Running the application in a terminal did indeed provide the actual reasons for failure.

In my case, a combination of a missing GeoIP Python module and my failure to properly follow the instructions(placing the conf fie in the wrong directory) were the cause. It's running well now (in test mode).

Thank you for your help and your fine policy server.You're Welcome.:smile:

> **anotherfakeID said:**
> P.S. would it not be better to pass this policy first under smtpd_recipient_restrictions rather than last? It seems a waste to do all the spam and content filtering when the entire transaction should have been dumped int the first place.This is up to you, I have it as the last check as I track ip's for spam and other "attacks" for reporting and logging purposes. Try it as first check if you wish.

Glad I could help.

---

