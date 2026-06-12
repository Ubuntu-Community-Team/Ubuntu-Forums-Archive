---
title: "cctv camera"
date: 2024-02-08
forum: Security
---

### Post by jgw on 2024-02-08
My current house cameras have gone bad.  They have been working for over 20 years so I am not surprised.  I have gone to ebay to take a look and they have lots of cctv cameras for the right price.  I suspect that most cctv cameras are pretty much the same.  I figure to setup 3 cameras.  None need to be outside but I will buy those that can go outside just to make sure in case I need to put them outside.  As far as I can tell most of the cameras broadcast and that broadcast can be accessed by the computer regardless of Microsoft or Linux.  I know, sketchy.

Anyway, I thought I would ask if anybody has any thoughts on this one before I spend my money.  I also notice that most being sold not that they work with Microsoft but assume and any computer that can get the signal will work.  

I would appreciate any thoughts on this one.  I hope I have put this in the right place.  If not I can move it.  

Thank you............

---

### Post by CharlesA on 2024-02-08
I have only tried one Raolink camera (RLC-410) in the past and them seem "OK" for the price. The one I had was able to be powered via power over ethernet or a barrel jack and could record to either an micro SDcard or an NVR.

I was trying to use BlueIris, which worked OK for me, but I was running it on an underpowered box, so it was a bit sluggish. That only ran on Windows, however.

I found a Linux alternative named Frigate, but I have not used that before. It's self hosted.

As far as the cameras go, I do not have any recommendations, but I would suggest keeping them on their own network, with no internet access to reduce the risk of them either phoning home or getting compromised somehow.

Only allow them to talk to the NVR and nothing else.

---

### Post by lu1g1 on 2024-02-09
thank you  I planning on building an NRV and will try to use Frigate

---

### Post by TheFu on 2024-02-10
Cameras are fraught with security considerations.  Cheaper cameras usually have some terrible-for-privacy mandates.  This is relatively recent since IoT stuff became a tracking/sales method.

Assume any camera that doesn't specifically say they work without internet requires internet connectivity for you to access it. Further, if you want to save any images/video, it likely has a monthly subscription required too.  By mandating internet connectivity, they can make access from remote locations possible on nearly any platform.  Really cheap cameras may have only a phone app for access - no website.  I have one of these cameras.  I expected there would be a website to allow access and I'd planned to setup an image snapshot cron job every minute to grab information.  Alas, it was only accessible using their standard app that tracks my phone.  They set the app permissions to require fine GPS location for some reason. Of course, I took the case off and looked at the insides. It was a cheap Chinese webcam with slightly customized firmware.  When I scan the device, there's no open ports to access any information through.

Beware.

To avoid these things, look for "IP cameras".  Expect to pay USD$100+ - probably $150/ea.  The better options seem to have POE, so you'll need network equipment that can inject the correct type of power for the camera requirements.  If you just want things to work and cost is a secondary consideration, Ubiquiti makes IP-cams and network equipment that does power over ethernet. [https://ui.com/us/en/camera-security](https://ui.com/us/en/camera-security)   I've never used their IP-cams, but I have used their wifi-APs and found them to be well-priced for their target capabilities (sub-enterprise, but beyond typical small business equipment).  There are certainly cheaper kits.

The recommendation to place these camera on a different subnet is smart and an FBI recommendation.  [https://www.fbi.gov/news/stories/cyber-tip-be-vigilant-with-your-internet-of-things-iot-devices](https://www.fbi.gov/news/stories/cyber-tip-be-vigilant-with-your-internet-of-things-iot-devices)

---

