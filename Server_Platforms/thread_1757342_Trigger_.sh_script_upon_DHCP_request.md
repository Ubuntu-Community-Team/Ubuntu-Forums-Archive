---
title: "Trigger .sh script upon DHCP request"
date: 2011-05-13
forum: Server Platforms
---

### Post by mihamil on 2011-05-13
Is there a way trigger a shell script after my DHCP server successfully gives out, either a specific IP address or to a specific MAC address.

I have two Xbox360's in my house that both receive IP address via DHCP reservations from the Ubuntu server.  

I have come to accept that without having two public IP addresses getting both to have an open NAT will be very difficult.  I have decided that I am OK with only one being able to have an Open NAT at a time, but I want to change the firewall rules according to which Xbox 360 turned on first.  This way I can move between level in my house and play online without having to modify rules manually.

---

### Post by highonv8splash on 2011-05-13
I'm not sure how to trigger a script on DHCP request, but perhaps you could just add the script as a cronjob to run frequently. It seems reasonable to quickly parse your dhcpd leases file to determine if the status of either xbox changed and/or which was turned on first.

---

### Post by mihamil on 2011-05-13
I have thought about that and will be giving it a try if there are no other ideas, but it seems like I would need the Cron job to run at least every 30 seconds to a 1 minute otherwise I may experience a wait time to get the rules changed upon changing Xbox's.  Do you think having a Cron job like this run that often would cause any performance issues on the server?  It is a dell optiplex GX 240 2.8 Ghz P4 with 512 MB of RAM.

I started working towards something but am not sure how to make it work. 

I set up a script that takes an input (which would be from the log files recording DHCP actions).  The input would only be DHCPACK log entries.  Then it uses cut to determine the ip address given and, using some simple if conditions determines which Xbox was turned on first.  Then it would be some simple commands to adjust the iptables rules.  My problem is how to constantly watch the log file and run the script each time the a new entry is put in.

I tried something like this

script file contains

while read inFile; then
   #DETERMINE WHICH RULES TO APPLY <--- This part is no problem
done

then start it using 

tail -f /var/log/message | myscript.sh

This doesn't seem to work.

When I copy a DHCPACK entry from the log and run it like this

echo "DHCPACK ENTRY FROM LOG CONTAINING IP ADDRESS GIVEN OUT" | myscript.sh

it successfully determines which xbox would have been on first. 

This indicates that my logic for determining the xbox is correct but getting the script to run with each entry is giving me problems.

I hope this makes sense.

---

### Post by mihamil on 2011-05-13
got it.  In the dhcpd.conf file you can execute scripts using the execute command along with the on commit event which will execute every time dhcp server commits an ip lease to a host.

host {
   etc;
   etc;
   on commit{
      execute("patch/to/script","commit","host")
   }
}

---

