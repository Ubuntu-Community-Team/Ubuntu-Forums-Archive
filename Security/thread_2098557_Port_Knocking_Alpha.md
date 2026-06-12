---
title: "Port Knocking Alpha"
date: 2012-12-27
forum: Security
---

### Post by KaosuX on 2012-12-27
UPDATE: New code has been released. These forums hate my comment formatting so just ignore the obvious odd formatting of my comments, haha.

Fort Knocks is one of a kind hybrid implementation of a technique known as "port knocking". My implementation has the exact same end-result as traditional port-knocking (Minus a few features due to it being in early development) except for the key fact that I use a single generic knock sequence to trigger an authentication process which is used to grant remote access.

Most traditional "port knocking" daemons will use the knock sequence itself as authentication. Personally, I think this is rather silly since the information can be easily sniffed by an attacker. Instead, I believe a better implementation is to operate under the condition that the sequence itself is already compromised and rely on a strong authentication system. 

While the "secret knock" it still in tact, I simply added a layer of security to the original process that works as a dynamic password-less authentication. A simple one-time configuration is all the user needs to get up and going!

I am not entirely sure what to call this type of implementation just yet. However,  it cannot be simply quantified as traditional port knocking.

```

########################################################################
#                          [Fort Knocks v1.0] #
########################################################################
# TODO:
#      1) Support IPV6.
#      2) Reload pre-existing IPTable rules upon closing.
#      3) Use AT to efficiently expire specific IPTable rules after n minutes. Specified by the user.
#      4) Move the knock_key into an encrypted file and If the key file does not exist, create one automatically.
#      5) Once a knock_key is generated, find a user-friendly way of helping the key file to the client.
#      6) Convert Fort Knocks into a daemon and move all output/logging to SYSLOG.
#      7) Optimize for better efficiency where possible (I know, the code is sloppy and not optimized well).
#      8) Fix all known bugs (I wonder if anyone notices them).
#      9) Do some heavy stress testing to gauge stability and improve it where possible.

#########################
# Import Libraries      #
#########################
import datetime
import dpkt
import pcap
import socket
from Crypto.Hash import SHA512
from Crypto.PublicKey import RSA
import os

#######################
# Configuration       #
#######################
interface = "wlan0" #Interface name. Check ifconfig or iwconfig for your settings..
open_command = "openup" #Command to allow remote access. Change this to whatever you want to use. It is always encoded.
close_command = "closeup" #Command to disallow remote access. Change this to whatever you want to use. It is always encoded.
backup_directory = "~/Desktop/iptable.rules" #Modify this to back iptable rules up at any location you want.

###########################
# Knock_key Configuration #
##########################################################
# Copy/paste your knock_key here for the time being.     #
# later versions will store this in an AES encrypted     #
# file on the server and client machine for added        #
# security.                                                #
##########################################################
knock_key = """
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
""" 

#################################################################################
# Build our initial encoded keys. We will need to rebuild them every time a new #
# authorized pre-authenticated session occurs due to us using a dynamic  salt.  #
# Having this section of code in both places will automatically expire keys     #
# that are older than 1 minute of being issued without causing issues.          #
#################################################################################
now = datetime.datetime.now() #Leaves this alone if you plan on using a time-based salt
salt = str(now.minute) #Create a salt that changes every minute. It may be predictable, but it changes often enough to ward off most attacks
        
securehash = SHA512.new(salt + knock_key) #Hash our knock_key with a salt. The client will be sending information in this exact format, so this is how we get ready to detect it.\
encoded_knock_key = securehash.hexdigest() 

securehash = SHA512.new(salt + encoded_knock_key + open_command) #Hash our open_command with a salt. The client will be sending information in this exact format, so this is how we get ready to detect it.
encoded_open_command = securehash.hexdigest() 
   
securehash = SHA512.new(salt + encoded_knock_key + close_command) #Hash our close_command with a salt. The client will be sending information in this exact format, so this is how we get ready to detect it.
encoded_close_command = securehash.hexdigest()
        
###########################################
# Initialize clean IPTables configuration #
###########################################
print "Backing up current IPTables configuration..."
os.system ("iptables-save > " + backup_directory) #Back rules up.
print "Flushing current IPTables configuration..."
os.system ("iptables -F") #Flush rules.
os.system ("iptables -X") 
print "Creating a new default-deny policy...."
os.system ("iptables -A INPUT -i lo -j ACCEPT") #Allow loopback.
os.system ("iptables -A INPUT ! -i lo -d 127.0.0.0/8 -j DROP") #Drop addresses which won't use loopback.
os.system ("iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT") #Allow established inbound connections.
os.system ("iptables -A OUTPUT -j ACCEPT") #Allow outbound traffic. Modify this for your personal needs. This will work for most people.
os.system ("iptables -A INPUT -j DROP") #Drop all incoming connections.
os.system ("iptables -A FORWARD -j DROP") #DROP forwarded requests.
print "Your new IPTables configuration is now active! Loading Fort Knocks...."

####################################
# Set up the interface and filters #
####################################
pcap=pcap.pcap(interface, 65535, 1, 0) #Load up the specified interface for sniffing, limit to 65535 bytes per packet, enable promiscuous mode, immediate should be left as default.
pcap.setfilter("tcp") #Sniff all TCP traffic.
print 'listening on %s' % (pcap.name) #Let the user know everything is running and working as intended (Remove this when Fort Knocks is made into a daemon)

for ts, buf in pcap:
    eth = dpkt.ethernet.Ethernet(buf)
    ip = eth.data #Header
    tcp = ip.data #Payload
    src_ip = socket.inet_ntoa(ip.src) #decoded source IP address
    dst_ip = socket.inet_ntoa(ip.dst) #Decoded destination IP address
    if (tcp.dport == 4144 and tcp.sport == 4414): #Look for a very specific destination and source port (This is our generic "knock"). I will add a way to customize this easier later on
        
        now = datetime.datetime.now() #Leaves this alone if you plan on using a time-based salt
        salt = str(now.minute) #Create a salt that changes every minute. It may be predictable, but it changes often enough to ward off most attacks
        
        securehash = SHA512.new(salt + knock_key) #Hash our knock_key with a salt. The client will be sending information in this exact format, so this is how we get ready to detect it.\
        encoded_knock_key = securehash.hexdigest() 

        securehash = SHA512.new(salt + encoded_knock_key + open_command) #Hash our open_command with a salt. The client will be sending information in this exact format, so this is how we get ready to detect it.
        encoded_open_command = securehash.hexdigest() 
   
        securehash = SHA512.new(salt +  encoded_knock_key + close_command) #Hash our close_command with a salt. The client will be sending information in this exact format, so this is how we get ready to detect it.
        encoded_close_command = securehash.hexdigest() 
        
    if encoded_open_command in tcp.data: #Valid command
       print "Command verification was successful! Granting access to the remote user!" #When this is a daemon it sill send messages like this to SYSLOG
       os.system ("iptables -A INPUT -s " + src_ip + " -j ACCEPT") #Add rule
    if encoded_knock_key and encoded_close_command in tcp.data: #Valid command
       print "Command verification was successful! Revoking remote hosts access!" #When this is a daemon it sill send messages like this to SYSLOG
       os.system ("iptables -D INPUT -s " + src_ip + " -j ACCEPT") #Remove rule
       #3. Log everything
       #4. Send notification to admin (NOT THE PERSON CONNECTING) that a new connection has been temporarily allowed.
```

---

### Post by samiux on 2012-12-27
> **KaosuX said:**
> I was looking around at the known port knocking implementations and I was really unhappy with a lot of them. Too many defeated their own purpose by building themselves from the ground-up doing things that contradicted the entire theory behind port knocking to begin with, while others used out-of-date cryptographic functions that are not very secure in today's world.

So, I got bored this afternoon and decided to make an updated port knocking tool. It will eventually be turned into a *nix daemon, but while i work out all of the core functionality, it will remain as-is.

I just wanted to get some peer review to see if anyone has suggestions. So far it is going in the right direction. I still need to fix a lot of things, increase security by using better authentication mechanisms and fortifying current mechanisms from various forms of attack. However, as-is, it still beats a lot of other implementations and it has only been developed for a total of 1 and a half hour(s).


Before I continue on, please tell me what you think. Read all of the comments in the code before reviewing the code itself. You might suggest I fix something that is already on my to-do list, and that would not help either of us.

Anywho, here it is:

```
########################################################################
#                         [Fort Knocks v.094]                           #      
########################################################################
# Fort Knocks is a free and open implementation of a popular 
# network authentication method known as "port knocking".    
#                                                              
# I personally did not like the other implementations that   
# were widely available. Most were poorly designed or used   
# really dated encryption/hashes that are not secure. The    
# goal of Fort Knocks is to provide the same functionality   
# found in popular port knocking implementations, but with   
# security in mind from the ground up.                       
#                                                              
# Fort Knocks is still in very early development and will    
# radically change over the course of its development. The   
# codebase as you see it now is experimental. However, it    
# does already show potential and can easily be modified for 
# greater security and functionality as I keep working on it!
#                                                             
# Some advantages to Fort Knocks are:                        
#                                                            
# 1) It uses the pcap library to sniff local interfaces instead of
#    trying to open a port to listen for incoming connections for
#    improved security (All ports are CLOSED!)               
#
# 2) It hashes the knock key using a strong hashing algorithm (SHA512)
#    and a dynamic salt, making it more resistant against several
#    different types of attacks (MITM, rainbow tables, etc). Using a
#    strong hash seems to gain some network efficiency without gimping
#    security. However, in the future, I do plan on beefing this up.
#
#  3) It can generate secure random knock_keys for each individual user.
#     my development version does not have this implemented right now,
#     but the default settings for all users will be as follows:
#
#     private = RSA.generate(8192)
#     knock_key = private.exportKey()
#
#     Once you generate your knock_key, you can copy it to the client
#     to complete your authentication configuration. This provides
#     strong security without impacting the end-user in real-world
#     operation. No passwords to remember, etc. Just a one-time
#     configuration process.
#
#   4) Future versions will automatically create a backup of your
#      current IPTable rules, flush your existing rules, and create
#      a basic default-deny policy when Fort Knocks is running. This
#      means automatic configuration through the trusted IPTables
#      interface. You will be able to easily modify the default rules
#      that Fort Knocks will use by default, and when the application is
#      closed it will restore your previous rules! This means you won't
#      have to worry about a messey configuration or losing your current
#      firewall configuration.
#
#   5) Software built with security, efficiency, stability and simplicity
#      in mind. My implementation leaves less to change than most and
#      sticks with widely available and tested libraries to ensure the
#      best possible user experience. With such a small amount of code 
#      doing all of the work, it makes auditing for security issues
#      much easier!
#
#   6) It will be released under the GPL and everyone can benefit from 
#      my work! Hopefully as the project matures, others will begin to
#      develop on the code as well.
#
#
#   I still have a lot of work to do, bugs to fix, features to implement
#   but most of the legwork is complete. I just wanted to get peer
#   opinions on my work so far. I probably already know what all needs
#   to be changed for this to be as secure and functional as I want it to
#   be, but I would love to hear opinions on the direction I am headed in
#   so far.
#
#
#   Port knocking may not be the most useful of security layers, but at least
#   I can bring it to anyone that might want to use it. On top of providing
#   a quality listening device for the "protocol", I will provide a client
#   with the codebase as well for easy operation.
#
#   Sincerely,
#       Michael (Kaosu)
#          <troopa at gmail dot com>
########################################################################

#########################
# Import Libraries      #
#########################
import datetime
import dpkt
import pcap
import socket
from Crypto.Hash import SHA512
from Crypto.PublicKey import RSA
import random
import base64

#######################
# Configuration       #
#######################
now = datetime.datetime.now() #Leaves this alone if you plan on using a time-based salt
interface = "wlan0" #Interface name. Check ifconfig or iwconfig for your settings.
salt = str(now.minute) #Create a salt that changes every minute. It may be predictable, but it changes often enough to ward off most attacks.
open_command = "openup" #Command to allow remote access. Change this to whatever you want to use. It is always encoded.
close_command = "closeup" #Command to disallow remote access. Change this to whatever you want to use. It is always encoded.

###########################
# Knock_key Configuration #
##########################################################
# Copy/paste your knock_key here for the time being.     #
# later versions will store this in an AES encrypted     #
# file on the server and client machine for added        #
# security.                                                #
##########################################################
knock_key = """
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
""" 

############################################################
# Encode all used data (DO NOT MODIFY IF YOU ARE UNSURE)   #
############################################################
securehash = SHA512.new(salt + knock_key) #Hash our knock_key with a salt. The client will be sending information in this exact format, so this is how we get ready to detect it.
encoded_knock_key = base64.standard_b64encode(securehash.hexdigest()) #The client will be encoding the hash with Base64.
 
securehash = SHA512.new(salt + open_command) #Hash our open_command with a salt. The client will be sending information in this exact format, so this is how we get ready to detect it.
encoded_open_command =  base64.standard_b64encode(securehash.hexdigest()) #The client will be encoding the hash with Base64.

securehash = SHA512.new(salt + close_command) #Hash our close_command with a salt. The client will be sending information in this exact format, so this is how we get ready to detect it.
encoded_close_command =  base64.standard_b64encode(securehash.hexdigest()) #The client will be encoding the hash with Base64.

####################################
# Set up the interface and filters #
####################################
pcap=pcap.pcap(interface) #Load the interface we will be sniffing for the incoming knock sequence
pcap.setfilter("tcp") #Only monitor TCP traffic. This will allow us to discard other protocol we won't be using. I may change this to read UDP-only for added efficency later on
print 'listening on %s' % (pcap.name) #Let the user know everything is running and working as intended (Remove this when Fort Knocks is made into a daemon)

for ts, buf in pcap:
    eth = dpkt.ethernet.Ethernet(buf)
    ip = eth.data #Header
    tcp = ip.data #Payload
    src_ip = socket.inet_ntoa(ip.src) #decoded source IP address
    dst_ip = socket.inet_ntoa(ip.dst) #Decoded destination IP address
    if (tcp.dport == 22796 and tcp.sport == 4500 ): #Look for a very specific destination and source port. I will add a way to customize this easier later on
        print "Knock sequence detected!" #When this is a daemon it sill send messages like this to SYSLOG
    if encoded_knock_key and encoded_open_command in tcp.data: #Valid command
       print "Command verification was successful! Allowing Source IP for one hour" #When this is a daemon it sill send messages like this to SYSLOG
       #Insert IPtable rules to allow connection from src_ip for 1 hour.
    if encoded_knock_key and encoded_close_command in tcp.data: #Valid command
       print "Command verification was successful! Denying all hosts!" #When this is a daemon it sill send messages like this to SYSLOG
       #Restore IPTable rules back to a default deny policy with no exceptions            
       #3. Log everything
       #4. Send notification to admin (NOT THE PERSON CONNECTING) that a new connection has been temporarily allowed.

```

Nice software, but your design is quite different from the original.  Your design is quite simple.  Please read [the original]("http://www.zeroflux.org/projects/knock") to make sure you understand it.

Samiux

---

### Post by KaosuX on 2012-12-27
> **samiux said:**
> Nice software, but your design is quite different from the original.  Your design is quite simple.  Please read [the original]("http://www.zeroflux.org/projects/knock") to make sure you understand it.

Samiux

The simple design is a choice, not a mistake. I wanted to keep the implementation simple to prevent possible unwanted functionality and security vulnerabilities. I do understand the concept quite well, but I have also made some choices in the initial design that differ slightly from some implementation references.

The only real functionality it is missing that some design references have is a way to specify specific knock sequences for specific ports. While this can be useful, it also does not directly fit within the scope of a simple design with emphasis on security. Adding this type of functionality would be rather simple; it is just a matter of personal preference at this current stage in development. Once I have worked out all of the issues with this simple implementation, that is will I will expand functionality, and likely offer an easy way to define multiple custom knock sequences that can force specific ports open. 

Keep in mind that following some of these design references will result in much weaker security. The original design states that the authentication mechanisms should be encoded to protect transport across potentially hostile networks. However, most of the design references usually don't include this - which makes the overall amount of implementations extremely pointless in nature, IMHO.

Thanks for the feedback. Like I said, this is still at a very early stage of development and will keep changing as I work on it. As of right now, the code you have looked at was less than 2 hours of development and some of that was documenting notes in comments, et cetera.

This does follow the absolute core of the design specification though. It meets the requirements of: A method of allowing someone to keep a default-deny list active (incoming connections dropped) and having a secure way to open up ports using a special sequence, code and set of commands that can be programmed for different events. The only thing I am currently missing is a way to define access to specific ports through a series of sequences.

Also, the "knock" does not have to be specifically designed as making connections to a slew of different ports. Sure, this was the original design, but things can always be adapted; this does not mean it does not achieve the same end-result. I instead choose to use a pre-defined set of ports to trigger a generic knock sequence, and then further authenticate the connection based on encoded keys and specific commands. In the end, I find my method to be more efficient because it does not lock me into weak authentication mechanisms that rely too much on the knock sequence being obscure enough that no one will figure it out.  Heck, even if you used this with the default knock sequence, an attacker would still not be able to gain access. To this attacker, all ports would still be closed and he would not even be sure if the software was running or not.

In the end, you really should not assume a person does not understand a concept simply because they choose to go a different direction than the original specifications. I find the original specifications to be poorly designed and believe my solution is more robust, user-friendly, secure and there is beauty in simplicity.

With how it is now, I could easily define access to specific ports based on specific commands. I would simply replace "openup" with something like "allowssh" and simply create a series of cases that match encoded commands.

I will always keep the overall design, though. A series of specific ports to initiate the knock sequence (something the person must know) and run under the assumption that an attacker could gain knowledge of the sequence itself. This way I place more emphasis on a real authentication mechanism. No command is processed unless it is properly encoded and send along with the private knock_key. So, even if the port sequence is compromised, the attacker would still need to revert the RSA key from a salted SHA512 hash to be able to correctly encode the knock_key, but then he would also need to revert each command from a salted SHA512 hash to gain the other half of authentication.  That is far more secure than almost any other design reference I have seen. I also like having allowed sessions that are only allowed pre a set amount of time (1 hour usually). If more time is needed, the user can use the client to open it back up for another hour. However, making the rules expire naturally protects users from themselves. Too many people will open up a port on a public network and then forget to remove it or issue the "close sequence". I like taking the user element out of decisions where possible, and time-limits that can be easily customized allow users to be protected from themselves in the long run. It also greatly minimizes the attack surface, because an attacker hijacking a Fort Knocks session would only have 1 hour to successfully exploit a running service (Assuming they hijacked it the second they noticed it), disable the software so it does not revert back to a global default-deny when the time expires, etc. Otherwise their access to the compromised service will be quickly revoked.

Maybe some people won't see this as "traditional port knocking" and that is fine. This is not a traditional implementation - it's better in many ways and will achieve the exact same end-result, but with better security instead of just being a trivial layer that many people think is not worth the overall effort.

---

### Post by samiux on 2012-12-27
> **KaosuX said:**
> The simple design is a choice, not a mistake. I wanted to keep the implementation simple to prevent possible unwanted functionality and security vulnerabilities. I do understand the concept quite well, but I have also made some choices in the initial design that differ slightly from some implementation references.

The only real functionality it is missing that some design references have is a way to specify specific knock sequences for specific ports. While this can be useful, it also does not directly fit within the scope of a simple design with emphasis on security. Adding this type of functionality would be rather simple; it is just a matter of personal preference at this current stage in development. Once I have worked out all of the issues with this simple implementation, that is will I will expand functionality, and likely offer an easy way to define multiple custom knock sequences that can force specific ports open. 

Keep in mind that following some of these design references will result in much weaker security. The original design states that the authentication mechanisms should be encoded to protect transport across potentially hostile networks. However, most of the design references usually don't include this - which makes the overall amount of implementations extremely pointless in nature, IMHO.

Thanks for the feedback. Like I said, this is still at a very early stage of development and will keep changing as I work on it. As of right now, the code you have looked at was less than 2 hours of development and some of that was documenting notes in comments, et cetera.

This does follow the absolute core of the design specification though. It meets the requirements of: A method of allowing someone to keep a default-deny list active (incoming connections dropped) and having a secure way to open up ports using a special sequence, code and set of commands that can be programmed for different events. The only thing I am currently missing is a way to define access to specific ports through a series of sequences.

Also, the "knock" does not have to be specifically designed as making connections to a slew of different ports. Sure, this was the original design, but things can always be adapted; this does not mean it does not achieve the same end-result. I instead choose to use a pre-defined set of ports to trigger a generic knock sequence, and then further authenticate the connection based on encoded keys and specific commands. In the end, I find my method to be more efficient because it does not lock me into weak authentication mechanisms that rely too much on the knock sequence being obscure enough that no one will figure it out.  Heck, even if you used this with the default knock sequence, an attacker would still not be able to gain access. To this attacker, all ports would still be closed and he would not even be sure if the software was running or not.

In the end, you really should not assume a person does not understand a concept simply because they choose to go a different direction than the original specifications. I find the original specifications to be poorly designed and believe my solution is more robust, user-friendly, secure and there is beauty in simplicity.

With how it is now, I could easily define access to specific ports based on specific commands. I would simply replace "openup" with something like "allowssh" and simply create a series of cases that match encoded commands.

I will always keep the overall design, though. A series of specific ports to initiate the knock sequence (something the person must know) and run under the assumption that an attacker could gain knowledge of the sequence itself. This way I place more emphasis on a real authentication mechanism. No command is processed unless it is properly encoded and send along with the private knock_key. So, even if the port sequence is compromised, the attacker would still need to revert the RSA key from a salted SHA512 hash to be able to correctly encode the knock_key, but then he would also need to revert each command from a salted SHA512 hash to gain the other half of authentication.  That is far more secure than almost any other design reference I have seen. I also like having allowed sessions that are only allowed pre a set amount of time (1 hour usually). If more time is needed, the user can use the client to open it back up for another hour. However, making the rules expire naturally protects users from themselves. Too many people will open up a port on a public network and then forget to remove it or issue the "close sequence". I like taking the user element out of decisions where possible, and time-limits that can be easily customized allow users to be protected from themselves in the long run. It also greatly minimizes the attack surface, because an attacker hijacking a Fort Knocks session would only have 1 hour to successfully exploit a running service (Assuming they hijacked it the second they noticed it), disable the software so it does not revert back to a global default-deny when the time expires, etc. Otherwise their access to the compromised service will be quickly revoked.

Maybe some people won't see this as "traditional port knocking" and that is fine. This is not a traditional implementation - it's better in many ways and will achieve the exact same end-result, but with better security instead of just being a trivial layer that many people think is not worth the overall effort.

Sounds good.

In my opinion, the one hour time limit can be optional as some administration work may need over night or days.

The "close sequence" or closing ports can be done after the client is leaving.

Keep going.

Samiux

---

### Post by KaosuX on 2012-12-30
New code has been released in the original post. Let me know what you guys think of the newest version.

This is still in very early development so the code-base is subject to change dramatically at any given time. However, all feedback is welcome.

---

