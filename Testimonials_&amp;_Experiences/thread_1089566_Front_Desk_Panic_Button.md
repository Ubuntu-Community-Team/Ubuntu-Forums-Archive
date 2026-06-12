---
title: "Front Desk Panic Button"
date: 2009-03-07
forum: Testimonials &amp; Experiences
---

### Post by Sander79 on 2009-03-07
Hello,

Recently I put together an ubuntu server, connected it to a usb panic button, webcam and leftover gsm cellular and installed it  behind the front desk at work. I did this because over the last months there were angry customers calling and making threats to my co-workers, as well as sending threatening email and letters. Even though there is an alarm present, it would take some time before security/police would arrive.

So when someone hits the button under the counter, the server will send emails to employees in the building, who can then check the website and see what's happening on the webcam and then call the police (and send the webcam internet address) and/or go to the front desk and using numbers against any unwanted visitors. The server also sends a message across the network using net send (winexe actually) alerting everyone and lastly it sends sms messages through the GSM.

Although it is not finished yet the 'prototype' is already active and functioning. I've used:

- nail for sending plaintext email (fastest way to go)
- gammu for sending group sms
- winexe for sending messages over net send (a popup many will see on windows desktops)
- webcam-server for grabbing and serving the webcam
- IBM thinkcentre desktop
- Creative QuickCam Sphere AF 640x480 (reasonable quality but cheap)
- Nokia 6310 and usb bluetooth dongle
- [http://www.giftmonger.com/acatalog/usb-panic-button-2.jpg](http://www.giftmonger.com/acatalog/usb-panic-button-2.jpg)

I would like to make a howto of it so other people can use it. Basically the end product would be an image of it which can be downloaded and installed. Currently I've used grabbing for the webcam but I'm going to redo that into live streaming so it will record and take large resolution pictures when someone hits the button. I would also like some help on writing a php page to easily add cellular numbers to the script (I'm new to php). And lastly I need some help in finding a cleaner way to activate the system (I used a nonsudo account to autologin in the shell because I couldn't get the button to work any other way, I'm new to linux/ubuntu). When it's complete it will also support sending sms through a modem, activate batch scripts on windows dekstops and using sound and lights to warn others in the building. After that I will try and make it into a mobile panic button anyone can use when intimidated or threatened by either collegues or customers.

So what should I do with it and where to post it?

---

### Post by armandh on 2009-03-07
it would be nice if the designated person to show up was about 6'6" 300 lb kevlar covered side arm toting well trained licensed or sworn scary guy.

with a name tag "resolution specialist"

edit
rather than create a target rich environment

---

### Post by Sander79 on 2009-03-07
> **armandh said:**
> it would be nice if the designated person to show up was about 6'6" 300 lb kevlar covered side arm toting well trained licensed or sworn scary guy.

with a name tag "resolution specialist"

I live in the Netherlands, guns are quite less common but I suppose if there's people with guns on the webcam the designated persons are instructed not to go there ofcourse. It's likely there are some weapons, but if 20 guys show up they can intimidate as a group.

Another function of the system is that it might prevent people harassing or abusing colleagues.

---

### Post by Mud.Knee.Havoc on 2009-03-07
What a cool hack. :)

---

### Post by MartyBuntu on 2009-03-07
> **Sander79 said:**
> After that I will try and make it into a mobile panic button anyone can use when intimidated or threatened by either collegues or customers.



What kind of war-zone do you work in?

I'd rather invest my efforts in looking for a new job.

---

### Post by K7522 on 2009-03-07
> **MartyBuntu said:**
> What kind of war-zone do you work in?

I'd rather invest my efforts in looking for a new job.

Regardless of if or how much overkill it is, it's an awesome hack.

Great idea man!

---

### Post by MartyBuntu on 2009-03-07
> **K7522 said:**
> Regardless of if or how much overkill it is, it's an awesome hack.



I guess. Sounds overly complicated where much more "low-tech" solutions would serve better.

But I agree, it is a good hack. Hopefully someone could use it in a reasonable application.

---

### Post by Sander79 on 2009-03-08
> **MartyBuntu said:**
> What kind of war-zone do you work in?

I'd rather invest my efforts in looking for a new job.

Actually I'm looking for a new job, but not because of any threats. The service provided is collecting payments for other companies, the office is shared with a bailiffs office. Maybe because of the financial crisis it's become harder for people to pay their bills and they act out their frustration on those taking their money. I've also noticed more aggression towards personnel at hospitals (angry family of patients) and teachers (angry parents) and more robberies at quickiemarkets and gas stations, those are the places it could be useful. I don't work in security, nor do I have any experience, I don't know if security is still all about sitting in front of 100 monitors and watching for something to happen or if they walk about carrying  netbooks, able to watch any cam and respond within a few seconds.

Is it a hack? I thought of it because of sms messages sent by nagios, it's strange servers get that much attention when they're down but personnel does not. One day my collegue introduced an ecobutton to me to save power, I already experimented at home with Motion, a webcam and GSM because of a recent housebreaking so I put it together when I heard about the threats.

---

### Post by Sander79 on 2009-03-08
> **MartyBuntu said:**
> I guess. Sounds overly complicated where much more "low-tech" solutions would serve better.

But I agree, it is a good hack. Hopefully someone could use it in a reasonable application.

It might look like overkill but all it is is 1 script that sends email, sms and netsend at the touch of a button plus ofcourse a grabber for the webcam. It took me a couple of days to put it together because I'm new to linux and tested a dozen other sms/mail/stream programs but I guess someone with more experience in linux could put it together from scratch in a few hours.

---

### Post by MartyBuntu on 2009-03-08
> **Sander79 said:**
> The service provided is collecting payments for other companies...

...the office is shared with a bailiffs office.

[SIZE="5"]WHAT?[/SIZE]

You work at a *collections agency* that shares office space with a *bailiff's office* and you're trying to set up some kind of "twitter"-esque security system? 

Buddy, you don't need SMS messaging...you need a concealed/carry permit.

---

### Post by Sander79 on 2009-03-08
Thanks for proving my point. Could we stay ontopic and not discuss financial services?

---

### Post by bapoumba on 2009-03-08
Please remember to keep the conversation civil, thanks.
One post removed.

---

### Post by 3rdalbum on 2009-03-09
I need something like that where I work. I work at a discount furniture shop :-)

---

