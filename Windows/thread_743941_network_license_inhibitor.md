---
title: "network license inhibitor"
date: 2008-04-03
forum: Windows
---

### Post by self-defence on 2008-04-03
Hi,

I've got a bit of a problem I've got a Win server that acts as a domain controller for the network of about 40 computers and also acts as a license server for some software.
Now my problem is that for another software we have got a volume license key but only for 15 users but I would like to have the software installed on all of the workstations but only have it run up to 15 times at a time. It would also help with network deployment.
Is there a server and client software that would allow me to set the number of times a software is used on the whole network and then prohibiting the use of more if the maximum number has been reached. So that the license agreement would not be breeched.

Anyone have any ideas on this?

Thanks for the help.

Bye

---

### Post by rickyjones on 2008-04-03
The only way I think for that to be possible would be for the software manufacturer themselves to create a program to do that, where their software package "check in" with the server to see if it is legally able to run.

I would recommend contacting the manufacturer and see if they can assist you with this.

I hope this helps!

Sincerely,
Richard

---

### Post by prshah on 2008-04-03
> **self-defence said:**
> Hi,

I've got a bit of a problem I've got a Win server that acts as a domain controller for the network of about 40 computers and also acts as a license server for some software.


I don't know of a software to do this per se; but in Linux you could easily write a small script that will "call home" to check the number of clients using the software, the either allow/disallow loading of the software. Once the software exits, the scrip again contacts the server to let it know that a license has been "freed".

Do you want this in Linux or Windows?

---

### Post by rickyjones on 2008-04-03
Thinking about this a little more I think you could do something similar, but easy to bypass.

Install the application on all computer. Create a batch script to launch the program. What this script would do is create a file on a shared drive when it is invoked. It will also check to see how many of these files on in the shared drive. If 15 are already present then it will present an error and exit. Otherwise it will continue to open the application. When the application exits the script will delete its temporary file from the shared drive.

-Richard

---

### Post by self-defence on 2008-04-03
Hi,

thank you for your quick reply.
Yes unfortunately this is a windows network while there are a few clients with linux and a few servers with linux the domain controller and license server is windows.
I've already contacted the manufacturer and they have replied that their software doesn't have this capability. The only thing that could be done is to have as many licenses as there are workstations, but since this is a school and there are never more then 15 people doing something at the same time in the same software there is no need and there are some other benefits that it would be better if any workstation can be used.

rickyjones -> please do tell me more about your idea... it sounds interesting. You're saying that just make a batch file that creates a file on a network drive (ws1_sw1,ws2_sw1,...) and every time the script is run it checks how many files there are in the folder and if the number is higher than the one set it exits if lower it runs the program.
I've never done something like that before and I'd need to see how batch scripts work but I think it could be done. If there is no problem with security so that someone could just delete the file form the drive or edit the script it should fine (the only thing I can think of is that they could run the software form its install dir directly and it would work). It might even be a better idea than a license server. So thanks for the great idea.

prshah -> thanks for giving it in the first place.

I don't know why I was sure that some software like that must exist. I thought I'd even read something about a software like that some ware.

Anyway thank you for your help if anyone has any ideas they are appreciated. 

Thanks and good night

---

### Post by rickyjones on 2008-04-03
> **self-defence said:**
> 
rickyjones -> please do tell me more about your idea... it sounds interesting. You're saying that just make a batch file that creates a file on a network drive (ws1_sw1,ws2_sw1,...) and every time the script is run it checks how many files there are in the folder and if the number is higher than the one set it exits if lower it runs the program.
I've never done something like that before and I'd need to see how batch scripts work but I think it could be done. If there is no problem with security so that someone could just delete the file form the drive or edit the script it should fine (the only thing I can think of is that they could run the software form its install dir directly and it would work). It might even be a better idea than a license server. So thanks for the great idea.


Here is a very simplistic view of what the batch file would like like:

```

@echo off
set some variables
get listing of remote dir
if listing > xx then goto error
else continue
echo computername >> text file in remote dir
call application
when app closes delete the file i created above
exit
:error
show error message to user and exit

```

I'd be able to help you more later but unfortunately I have to run right now.

Sincerely,
Richard

---

### Post by self-defence on 2008-04-04
rickyjones -> Cool thanks... there's actually no big rush here since I still have to figure out lot's of other things before I beguine to standardize the whole network. My idea is to just setup one workstation and then just duplicate it to other workstations since the hardware is the on all of them.

Thanks again

Bye

---

### Post by rickyjones on 2008-04-04
> **self-defence said:**
> rickyjones -> Cool thanks... there's actually no big rush here since I still have to figure out lot's of other things before I beguine to standardize the whole network. My idea is to just setup one workstation and then just duplicate it to other workstations since the hardware is the on all of them.

Thanks again

Bye

Send me a PM or an email (richard@rrcomputerconsulting.com) in the future and I'll gladly work with you on setting up a script to take care of this.

-Richard

---

