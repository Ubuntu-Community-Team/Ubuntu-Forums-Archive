---
title: "Hardware requirements"
date: 2011-11-05
forum: Ubuntu Cloud and Juju
---

### Post by ELMIT on 2011-11-05
Currently I am just testing the cloud on the stick version. 

I have a couple of older computers here around and will start to use them in the next step.

Reading some documents (Ubuntu Enterprise Cloud Architecture - August 2009) I see that I need at least three computers whereby the CLC and WS3 is on one computer and CC and EBS is on one computer and the third one (NC) should be a good one. Multiples are better.

Q:
1. Which CD do I use to install each of these computer?
2. How do I distinguish CLC and WS3 on one computer? (or CC and EBS ?) Or others said, if I want to use 4 computers, what do I need to do?
3. Assuming I could manage above, how can a user use the cloud?
4. What are the requirements for the user's hardware? Would a tablet pc work? Would an iPhone work?
5. How can I manage resources for users?

What should I read to avoid too many questions here?

bye

Ronald

---

### Post by simpe_user on 2011-11-10
> **ELMIT said:**
> Currently I am just testing the cloud on the stick version. 

Q:
1. Which CD do I use to install each of these computer?
2. How do I distinguish CLC and WS3 on one computer? (or CC and EBS ?) Or others said, if I want to use 4 computers, what do I need to do?
3. Assuming I could manage above, how can a user use the cloud?
4. What are the requirements for the user's hardware? Would a tablet pc work? Would an iPhone work?
5. How can I manage resources for users?

What should I read to avoid too many questions here?

bye

Ronald
A
1 best way install from repository, but if you decide install from CD use single one for all computer installations, select right check-box accordingly you needs   
2 
   install eucalyptus-cloud on first computer 
   install eucalyptus-cc on second 
   install eucalyptus-sc on third
   install eucalyptus-walrus on fourth
3 user need following [http://open.eucalyptus.com/wiki/EucalyptusGettingStarted_v2.0](http://open.eucalyptus.com/wiki/EucalyptusGettingStarted_v2.0)
4 any hardware where you can run euca2ools commands. It is python based so if you can Python with boto lib on iPhone it can run.
5 You can install limitations to instances types or ebs volume and IPs per group through web interface

You should read open.eucalyptus.com site, and all documentation on it.

---

### Post by ELMIT on 2011-11-10
Thank you very much. It helps me a lot.

I also found many places to read and the picture is getting more and more clearer.


I have still some beginner questions:

The typical setup can be a two / three / four / .... machine
I wonder if I can have the NC local in my office and the others on Amazon?

I think of setting up (a) powerful NC(s) in my office to have a good working environment and could use some instances for other things, like a database server, mail server, ... AND an Asterisk (VoIP) server.
As I understand I can so use the hardware better without having to invest for new machines, when I need a new server.


That brings me to the next question. Assuming I can setup an Asterisk server, which should be as small as possible. How can I create an image, just for Asterisk? Is such image even already available?

Since the image decides what you are running, is it possible to setup a Windows image within an Ubuntu Cloud?
Assuming that would work too, would it be possible that a client works on two cloud instances? Ubuntu and Windows and could the client exchange data between these clouds via his clients?

---

