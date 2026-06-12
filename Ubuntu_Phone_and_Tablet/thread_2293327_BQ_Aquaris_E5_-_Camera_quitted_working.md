---
title: "BQ Aquaris E5 - Camera quitted working"
date: 2015-09-04
forum: Ubuntu Phone and Tablet
---

### Post by miuqom2 on 2015-09-04
After the last system updated yesterday, when I opened the camera application, I was asked to grant approval to share my pictures. I denied. 
Then application started but I don't have the "shoot" button enabled anymore, neither in camera mode nor video. 
Other buttons, which were previously available, like HDR, disappeared.
I tried to uninstall and install the application back, but nothing changed: I can't take pictures now.
Also the screen is black, like I had problem with the physical camera, but it's the same if I turn to the front camera.

Does anyone experienced the same problem? What can I do to have my app back working?

---

### Post by howefield on 2015-09-04
Try System Settings > Security & Privacy > Other App access > Camera and revert your choices.

---

### Post by coffeecat on 2015-09-04
> **miuqom2 said:**
> I was asked to grant approval to share my pictures. I denied.

As a point of information, the message does not mention sharing at all. After the recent upgrade, one sees this message when the camera app is first opened:

> Application camera is trying to access CameraService

Clearly, that needed to be allowed. Hopefully, the setting howefield pointed you to will sort this out.

---

### Post by miuqom2 on 2015-09-04
Super fast and working solution. Thanx.
CarmeraService, could be whatever for me though, I though about a sharing service. 
A more meaningful definition in the alerting message would have been better   :-)

---

### Post by howefield on 2015-09-04
> **miuqom2 said:**
> CarmeraService, could be whatever for me though, I though about a sharing service. 
A more meaningful definition in the alerting message would have been better   :-)

Lol, feel free to file a bug in launchpad suggesting an alternative, but CameraService to me seems to be a very apt description and imho most people would not expect the camera to work (as designed) if denied access to something called the "CameraService" :)

---

### Post by grahammechanical on 2015-09-04
We need to understand the security model of Ubuntu Phone.

1) The OS is read only.
2) Apps run in confinement. Apps cannot do stuff they are not authorised to do.
3) If an app seeks to access information the request has to pass through what is called the Content Hub. And then the user has to authorise the access to that part of the system.

It is this kind of security model that stops a game app or any app from accessing the user's Contacts List or Pictures folder or whatever, and uploading the information to someone else's computer without the user knowing about it. The app that controls the camera hardware has to conform to the same security model as every app.

It puts the user in control.

Regards.

---

