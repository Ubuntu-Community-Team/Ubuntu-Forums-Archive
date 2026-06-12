---
title: "Nagios E-mail notification"
date: 2010-08-12
forum: Server Platforms
---

### Post by Thyagaraj on 2010-08-12
I've installed Nagios monitoring tool but I couldn't configure E-mail notification to gmail.
plz any one help me...

---

### Post by spynappels on 2010-08-12
I had problems with this too when I set it up, but I found a Python script which could use a gmail smtp server to send emails and it worked perfectly. Can't remember where I got the script and I no longer admin that section so cannot look it up easily, but a google search for Python gmail script should help you out.

---

### Post by Thyagaraj on 2010-08-12
Oh! it's my bad luck. ok, I'll check in the google for that script..

Thank you

---

### Post by spynappels on 2010-08-12
Found it.

[http://exchange.nagios.org/directory/Plugins/Uncategorized/Operating-Systems/Linux/Nagios-Alerts-via-gmail-and-python/details](http://exchange.nagios.org/directory/Plugins/Uncategorized/Operating-Systems/Linux/Nagios-Alerts-via-gmail-and-python/details)

That's what I used.

---

### Post by Thyagaraj on 2010-08-12
I'm getting following error when i ran the script


Traceback (most recent call last):
  File "Downloads/./send_gmail.py", line 61, in <module>
    main()
  File "Downloads/./send_gmail.py", line 44, in main
    Addresses = address.split(',') #turns string into array by splitting string at commas.
AttributeError: 'NoneType' object has no attribute 'split'

---

### Post by spynappels on 2010-08-13
Are you sending notification to multiple email addresses or just to one? If multiple addresses, can you try sending to just one address and see if that works?

I am no Python expert, but it looks to me like it does not like the way some list of variables is separated.

---

### Post by Thyagaraj on 2010-08-13
No I just modified the mail part to my single gmail id and i dont even understand those errors
 
here is the script



#!/usr/bin/python 
import string, os, sys, time  
import os.path 
import smtplib 
from optparse import OptionParser 
import optparse 
 
""" 
This quick and dirty script can be used to send email messages from command line using a gmail account. 
It was designed to be a simple replacement for the default mail program (sendmail) used by Nagios. 
You must configure this file to work with your gmail account... 
Note: this script may be unsecure as the password is stored as plain text in the script. 
 
Requires smtplib, python 2.4.4c1+ and optparse 
 
Usage: 
send_gmail.py -a [to address] -s [subject] -b [message body] 
 
New lines can be inserted in the message body by using   \nnn  
Multiple to addresses must be seperated by commas (a space character may preceed and/or follow the comma) 
 
Example: 
send_gmail.py -a "someone@somedomain.null,someone@smsgateway.null" -s "This is the subject line..." -b "Body line one\nnnAnd this is line two" 
 
code based on [http://mail.python.org/pipermail/python-list/2007-January/423569.html](http://mail.python.org/pipermail/python-list/2007-January/423569.html) 
 
**Update/Revision History** 
2008.04.09 - Version 1.0.1 posted, fixed problem where script would not handle multiple recipents, 
smtplib's .sendmail() requires an array to send to multiple addresses. If all addresses are passed as a string, it will only send to the first address. 
 
2008.01.24 - Version 1.0.0 posted 
 
""" 
 
def main(): 
    p = optparse.OptionParser( ) 
    p.add_option('--address', '-a', action='store', type='string') 
    p.add_option('--body', '-b', action='store', type='string') 
    p.add_option('--subject', '-s', action='store', type='string') 
    options, arguments = p.parse_args() 
    
    body = options.body 
    address = options.address 
    Addresses = address.split(',') #turns string into array by splitting string at commas. 
    subject = options.subject   
     
    body = '\n'.join(body.split('\\nnn')) 
             
    server = smtplib.SMTP('smtp.gmail.com', 587) 
    server.set_debuglevel(1) #0 for quiet or 1 for verbosity 
    server.ehlo('thyagaraj@gmail.com') 
    server.starttls() 
    server.ehlo('thyagaraj@gmail.com')  # say hello again 
    server.login('thyagaraj@gmail.com', 'mygmailpassword') 
     
    server.sendmail('thyagaraj@gmail.com', Addresses, "Subject: " + subject + '\nTo:' + address + '\n\n' + body) 
     
    server.quit() 
 
if __name__ == '__main__': 
    main()

---

