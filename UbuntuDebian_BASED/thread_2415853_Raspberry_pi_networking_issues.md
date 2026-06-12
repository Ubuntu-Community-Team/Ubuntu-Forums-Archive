---
title: "Raspberry pi networking issues"
date: 2019-04-01
forum: Ubuntu/Debian BASED
---

### Post by clinquist on 2019-04-01
I apologize in advance if I'm posting in the wrong section, and I understand that Ubuntu and Raspbian are not identical.  
But I can't find the answers I need on the Raspberry forum, so I thought that a more general linux area might get the attention of someone who could help.

That said...


I'm using a Raspberry pi to connect to a reverse SSH tunnel setup on an Amazon ec2 server.  And I'm using a 4G/LTE USB "dongle" to provide the connectivity.

The "dongle" looks like  eth0 or eth1 to the Raspberry pi and will usually connect to the carrier (Verizon) during boot.  I had to add a "SLEEP 16" command in  rc.local  because the modem boots more slowly than the Raspberry 3 (running STRETCH), and the delay gives the modem a chance to boot and make connection to the 4G/LTE network.

But I have two problems that I can't seem to figure out:

Problem #1.  The Raspberry sometimes hangs at the   
"A start job is running on dhcpcd on all interfaces (xx/yy)"   (where "xx" and "yy" are times).  On _some_ power ups, the system simply hangs at this point forever. Only a power cycle will allow recovery.

Problem #2. Even after a connection has been made, the 4G/LTE signal sometimes gets blocked or very weak and re-appears a few seconds to a few minutes later. I need the Raspberry to automatically reconnect to the Amazon server (over SSH) anytime a connection is possible.   The USB "dongle DOES reconnect to the cell network - I can ping servers, etc. After the dongle (modem) reconnects.  Everything works except the SSH connection.  I loaded AUTOSSH (rather than just SSH) in an attempt to fix this, but it doesn't work (regardless of the timeouts I select).  I should mention that I have no control or "ping" port available on the Amazon server. 
It should be noted that if I manually invoke AUTOSSH  after the connection is re-established, everything works as expected.

In an attempt to solve issue #2, I set up a WATCH command that pings GOOGLE (8.8.8.8) every 5 seconds, and if the ping is successful it checks for the presence of a file, and if that file is present,  it invokes AUTOSSH and writes that file ( in memory ).  If the ping is not successful, the file in memory is deleted.  That way, when the system first comes up, it issues AUTOSSH and writes the file.  Every 5 seconds thereafter, it pings 8.8.8.8 and if that ping is successful, my script does nothing.  If the ping is NOT successful, the file is deleted, so that the next time the ping IS successful, the file won't exist and AUTOSSH will be started again.
It ALMOST works.  But it doesn't and I'm stumped.  I suspect that the WATCH command expects to call an actual command, rather than a shell script, but I don't know for certain.

Can anyone help me solve these two problems?  I would greatly appreciate it.  I'll include the contents of my files below:

rc.local
################################################
 sleep 16                                                                 <--- wait for the USB dongle to boot
 ifdown -a && ifup -a                                                <-- shut off and turn on ports, this seems to make 1st startup more reliable

    watch -n 5 /home/pi/runonce.sh                              <--- call 'runonce' every 5 seconds.

exit 0
#########################################################

/home/pi/runonce.sh
#########################################################
ping -c1 8.8.8.8                                                  <-- Google server
if [ $? -eq 0 ] ; then                                              <-- good ping
  [ -f /dev/shm/keyfile ] || {                                    <-- check for file 'keyfile" in RAM (in a Raspberry pi)
    /home/pi/start-autossh.sh &                                 <-- keyfile not found, so run AUTOSSH
    touch /dev/shm/keyfile                                         <--- create keyfile
    sudo python /etc/LEDON.py                                   <--- turn LED on to indicate connection
}
else
    sudo rm /dev/shm/keyfile                                     <-- ping was not good, delete keyfile
    sudo pkill /home/pi/start-autossh.sh                       <-- kill instance of autossh if it is still running
    sudo python /etc/LEDOFF.py                                   <-- turn LED off to indicate lost connection
fi
exit 0
#########################################################

Note that these problems do not occur if I connect an Ethernet cable to either the Raspberry's Ethernet port, or to an Ethernet<->USB adapter plugged into a Raspberry's USB port.

If someone could point me to a log file that would tell me what is going on, that would be of help also.

---

### Post by QIII on 2019-04-01
Moved to Ubuntu/Debian BASED as a more appropriate sub-forum.

Not to worry.  Your title will surely grab some attention.  A lot of us are very interested in SBCs.

---

