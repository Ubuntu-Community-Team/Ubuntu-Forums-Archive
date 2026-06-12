---
title: "Script for windows client machine."
date: 2016-01-05
forum: Server Platforms
---

### Post by gardenair on 2016-01-05
[TABLE="width: 100%"]
[TR]
[TD]hi,
I have configured my samba server in ubuntu box. The samba share is connected with the clients computers running windows 7. I want that when ever the users enter into the drive (means they double click on map drive i.e Z drive),  at 5:45 pm it show the users that the server is going to off and if the users does not enter into the map drive whole day  it does not show any alert message on the client computer i.w windows 7.

Is there any way in samba that can help me ?

*In windows I just create a simple script file and keep it in "Tash Scheduler"*
```
x=MsgBox("The File Server is going to Shutdown.Please save your data", 48+16, "Box Title")

```Save the script file shutdown.sh and keep . 

Can Linux can do something here or I should do it on the windows side ?

thanks[/TD]
[/TR]
[/TABLE]

---

### Post by MAFoElffen on 2016-01-06
Idea? From the Samba server, you should be able to use this script as a cron job
```

#!/bin/bash
smbclient -M 192.168.0.255 <<EOF
The File Server is going to Shutdown.Please save your data
EOF

```
Explanation-- Using the messenger service of smb client, use the network broadcast ID to send a message to all Samba users. I know using a specific ip or netbios name works, but guessing that, logically, using the broadcast ID should also work.

---

### Post by gardenair on 2016-01-06
Thanks "[COLOR=#000000]MAFoElffen" [/COLOR] for the reply....please can you explain about "[COLOR=#000000]messenger service of smb client," Does it mean the windows client computers whicg are running windows 7 or 8 ? or it is a part of samba server ? I have 5 clients computers  so instead to give broadcast  address how can I add that specific addresses ?[/COLOR]

---

### Post by MAFoElffen on 2016-01-06
the Smb filesharing protocol uses some network messengers services that Windows machines also use to communicate between machines. That way, a local machine can talk with a remote machine to see if it is part of a workgroup, has any shared resources, etc. Using those same connections, Samba client can also use the messenger service to talk with one another informally, beyond what it just needed to share files and resources. Anyone (Linux, Unix, Windows, etc) using smb services are in-part, communicating to each other in a common language, with common services shared between each other (to allow that to happen). The smb messenger service is just one of the pieces of that.

As an alternative, some admins can also use telnet to send messages between Unix, Linux and Windows machines... which is default in Linux and Unix boxes, but would have to be turned on as a feature on any Windows Boxes. I think using the smbclient as a messenger is better solution, as turning on telnet is just one more thing to administer and keep going... where smb services are already there when you are sharing using smb services.

As an aside, a network broadcast address is an address on a network segment that is shared between all members of that network segment. There is also a broadcast address for "global" ... which means will broadcast across routers, to all networks. That is not one you want to use to send a message...

---

### Post by gardenair on 2016-01-06
Well appreciate your kind reply.As for this it is a new thing for me to send a message from samba server.Thanks to samba team that they build such a nice  protocol in which  Linux and Windows computers communicate with each other. As to your previous post the script which you have mention is nice. Is there any proper location where I keep this script file say "client_message.sh"
Add path in crontab -e with proper timing.
I should be glad if you may kind elaborate it a bit  more. 

thanks.

---

### Post by MAFoElffen on 2016-01-06
```

#start the cron job editor
sudo crontab -e
# add your job with these parameters, explained below
45 17 * * 1-5 /home/userName/cron_jobs/samba_save_warning.sh

```
MIN (Minute field) - 45th minute of the hour
HOUR (Hour field) - 17th hour of the day, 5:45pm
DOM (Day of Month) - *, all dates are valid
MON (Month field) - *, all months are valid
DOW (Day Of Week) - 1-5, Monday, Tuesday, Wednesday, Thursday, Friday (All weekdays)
CMD (Command) - /home/userName/cron_jobs/samba_save_warning.sh, path to and command to execute the script

So would schedule/execute it every work/week day at 5:45 pm... Remember to change the script's file attributes to executable.

Enough info?

---

### Post by gardenair on 2016-01-07
Well on my client computer samba server is working.For just for test purpose i use my own computer  IP address i.e 192.168.1.50 and save it on /home/message.sh file (The file is on the server)


```
#!/bin/bash
smbclient -I 192.168.1.50 <<EOF
The File Server is going to Shutdown.Please save your data
EOF

```

give it full right 

```
# chmod 777 message.sh
```

add the code in crontab -e

```
00 12 * * * /home/message.sh
```

it not show me any response:-k

---

### Post by MAFoElffen on 2016-01-07
I set my scripts to either of these:
```

chmod 755 message.sh
chmod +x message.sh

```
Test the script from the commandline first
```

/home/message.sh

```
If it works from the command line, then setup in cron, after it should execute, if you do not get a test response, check the syslog to see what the log said...
```

dmesg | grep -i cron

```

EDIT-- As after thought... There was something I remembered concerning this from the Samba Mailing list from a few years ago. I looked it up and... add bash to the command to force the script to run in a bash session. It has to do with how cron runs and how smbclint needs to run in a session... so in crontab:
```

00 12 * * * bash /home/message.sh

```

---

### Post by gardenair on 2016-01-07
Well there is a problem in the script which u have mentioned

```
#!/bin/bash
smbclient -I 192.168.1.50 <<EOF
The File Server is going to Shutdown.Please save your data
EOF

```


I write another simple script (just for test purpose) and execute it in my terminal it works
```
#!/bin/bash
# My first script
echo "Hello World!"

```


I think the script for smbclient need s to review...

---

### Post by MAFoElffen on 2016-01-08
From man smbclient:
> 
-M

This options allows you to send messages, using the "WinPopup" protocol, to another computer. Once a connection is established you then type your message, pressing ^D (control-D) to end. (without user interaction) You could also pipe it through and cat or echo it through the pipe.

If the receiving computer is running WinPopup the user will receive the message and probably a beep. If they are not running WinPopup the message will be lost, and no error message will occur.

The message is also automatically truncated if the message is over 1600 bytes, as this is the limit of the protocol.

One useful trick is to cat the message through smbclient. For example:
cat mymessage.txt | smbclient -M FRED

will send the message in the file "mymessage.txt" to the machine FRED.

You may also find the -U and -I options useful, as they allow you to control the FROM and TO parts of the message.

See the message command section of smb.conf(5) for a description of how to handle incoming WinPopup messages in Samba.

Note: Copy WinPopup into the startup group on your WfWg PCs if you want them to always be able to receive messages.


-I IP number

IP number represents the IP number of the server to connect to. It should be specified in standard "a.b.c.d" notation.

Normally the client will attempt to locate the specified Lan Manager server by looking it up - that is, broadcasting a request for the given server to identify itself. Using this parameter will force the client to assume that the server is on the machine with the specified IP number.

There is no default for this parameter. If not supplied, it will be determined automatically by the client as described above.

Sorry. -M now wants the NetBIOS name, where I think previously, you could use either...

Here is some more references and some script examples:
[https://www.bentasker.co.uk/images/Documentation/06_sending_receiving_and_broadcasting_winpopup_messages_on_linux.pdf](https://www.bentasker.co.uk/images/Documentation/06_sending_receiving_and_broadcasting_winpopup_messages_on_linux.pdf)
[http://www.cyberciti.biz/tips/freebsd-sending-a-message-to-windows-workstation.html](http://www.cyberciti.biz/tips/freebsd-sending-a-message-to-windows-workstation.html)
[https://www.zabbix.com/forum/showthread.php?t=2147](https://www.zabbix.com/forum/showthread.php?t=2147)

If you open a Linux terminal and type the sole command
```

smbclient -M Fred

```
it will prompt the user to type a message, and at the end, indicate that (end the message) by pressing <cntrl><D>. That is also the character for End Of File (EOF). The script written that way says echot the following until, up to and including the EOF marker...

The above links are further and differing examples of hwo to do that... including that first link that is more detailed.

I have to admit, that I did that from memory. Now that I try to test that from my Samba server, to a Windows 10 box... before it sends a message, it asked me for a password(???) Not sure if that is a Windows 10 thing. I just upgraded some machines to Win10 within the last 2 weeks, so that is new to me and I will have to investigate what is going on with that.

---

### Post by MAFoElffen on 2016-01-08
From man smbclient:
> 
-M

This options allows you to send messages, using the "WinPopup" protocol, to another computer. Once a connection is established you then type your message, pressing ^D (control-D) to end.

If the receiving computer is running WinPopup the user will receive the message and probably a beep. If they are not running WinPopup the message will be lost, and no error message will occur.

The message is also automatically truncated if the message is over 1600 bytes, as this is the limit of the protocol.

One useful trick is to cat the message through smbclient. For example:
cat mymessage.txt | smbclient -M FRED

will send the message in the file "mymessage.txt" to the machine FRED.

You may also find the -U and -I options useful, as they allow you to control the FROM and TO parts of the message.

See the message command section of smb.conf(5) for a description of how to handle incoming WinPopup messages in Samba.

Note: Copy WinPopup into the startup group on your WfWg PCs if you want them to always be able to receive messages.


-I IP number

IP number represents the IP number of the server to connect to. It should be specified in standard "a.b.c.d" notation.

Normally the client will attempt to locate the specified Lan Manager server by looking it up - that is, broadcasting a request for the given server to identify itself. Using this parameter will force the client to assume that the server is on the machine with the specified IP number.

There is no default for this parameter. If not supplied, it will be determined automatically by the client as described above.

So -M [NetBIOS HostName]... It seems to want a NewtBIOS name. Sorry, I think oprevious versions could use NetBIOS and IP interchangibly... 

Here is some more references and some script examples:
[https://www.bentasker.co.uk/images/Documentation/06_sending_receiving_and_broadcasting_winpopup_messages_on_linux.pdf](https://www.bentasker.co.uk/images/Documentation/06_sending_receiving_and_broadcasting_winpopup_messages_on_linux.pdf)
[http://www.cyberciti.biz/tips/freebsd-sending-a-message-to-windows-workstation.html](http://www.cyberciti.biz/tips/freebsd-sending-a-message-to-windows-workstation.html)
[https://www.zabbix.com/forum/showthread.php?t=2147](https://www.zabbix.com/forum/showthread.php?t=2147)

If you do the sole command from a terminal (by hand), it will ask you to type a message, then hit

---

### Post by MAFoElffen on 2016-01-08
[http://www.linuxquestions.org/questions/linux-networking-3/is-it-possible-to-send-and-receive-net-send-messages-in-linux-267067/](http://www.linuxquestions.org/questions/linux-networking-3/is-it-possible-to-send-and-receive-net-send-messages-in-linux-267067/)
BUT, note the date, which means ... **[COLOR=#ff0000]Nevermind[/COLOR]** ... trying to use the windows alerter service anymore. After Win XP, MS removed some of the pieces of that for security reasons. Use telnet instead.

Testing that for you between my Samba Server and a Windows 10 box... Back soon with the results...

---

### Post by MAFoElffen on 2016-01-08
Okay... after some research.

telnet won't work because you have Windows clinets, not a windows server, so you would not have a telnet seerver feature to turn on (nothing with a listener, waiting for for anyone to call to...

linpoopup and smbclient won't work, because Windows removed messenger service and winpopup, because of malicious exploits.  After MS did that, then smbclient stopped working to newer Windows clients, but still works to older clients. That does not help you for Win 7.

Windows added a msg.exe uitilty to Vista on, where windows clients can lan msg each other. It is locked down so that it can only go from Windows to Windows machines. But there is a possibility with that. Powershell has a PSExec cmdlet to execute Windows commands from a prompt or Powershell script. Linux has a binary package called winexe that can connect to a Windows box and execute a command.

- winexe binary would have to be dl'ed, compiled and installed. Once installed, a bash script could use that to call a windows box to execute a powershell command or PS Script to use msg.exe to broadcast your message to your other windows boxes. or that matter, since you are just going win to win, then you can net send to go to a usergroup that you create that is just windows Samba users. 

- Powershell scripts are not executable by default in Windows, so that feature would have to be turned on, on that box. That would open the permission to do that. You do that with the Powershell Set-ExecutionPolicy Cmdlet. 

So not pretty and a lot of pieces. Sort of a round about way to implement a solution ... but still possible. That is, until too many ill-intents exploit that, and then port gets removed/closed.

BUT--> To simplify "everything"... you have Windows 7 boxes = You could use Windows "Task Scheduler" to schedle a job to send the same message broadcast to all your Windows machines (like to a user group), without having to go Linux to Windows... For and Linux Users, if need be, you could do same doing Bash > XMessage | crontab.

---

### Post by gardenair on 2016-01-11
Well I have tried a lot.....play ,google a loot  but at the end...nothing.

Well I have just tried this but it show NT_STATUS_IO_TIMEOUT

```
# smbclient -M 10.1.83.250 
Enter root's password: 
Type your message, ending it with a Control-D
Hi,....I am samba server....
cli_message returned NT_STATUS_IO_TIMEOUT

```

The windows firewall is off,Samba share is working....but....I think the easiest way is to use "[COLOR=#000000]Task Scheduler" ...this will make life easy...otherwise from Linux to Windows sending a message is ........... which I understand [/COLOR]](*,)

---

### Post by MAFoElffen on 2016-01-11
> **gardenair said:**
> Well I have tried a lot.....play ,google a loot  but at the end...nothing.

Well I have just tried this but it show NT_STATUS_IO_TIMEOUT

```
# smbclient -M 10.1.83.250 
Enter root's password: 
Type your message, ending it with a Control-D
Hi,....I am samba server....
cli_message returned NT_STATUS_IO_TIMEOUT

```

The windows firewall is off,Samba share is working....but....I think the easiest way is to use "[COLOR=#000000]Task Scheduler" ...this will make life easy...otherwise from Linux to Windows sending a message is ........... which I understand [/COLOR]](*,)
Yes @ Task Scheduler. My answer implied the same in post #13

Still possible from Linux to a Windows client, but not using smbclient and not "directly." (see post #13)

 - Easier for Windows clients is from Task Scheduler to fire off a Powershell script that would make a net send or msg call to convey your message.  
 -- if you use net send, you can send to a user group, that you can create just for Samba users... but that would be for domain policy. If no domain, then have your PS script loop in a foreach (in your list) to send to a list of users.

---

### Post by gardenair on 2016-01-12
Thanks all for guiding me. ...

---

