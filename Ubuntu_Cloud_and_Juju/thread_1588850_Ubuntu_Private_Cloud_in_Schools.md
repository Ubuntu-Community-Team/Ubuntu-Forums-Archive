---
title: "Ubuntu Private Cloud in Schools"
date: 2010-10-05
forum: Ubuntu Cloud and Juju
---

### Post by webworldx on 2010-10-05
Hi folks,

Here goes what could be either a simple answer that I'm misunderstanding or the start of a great debate (apologies for either!)

Can anyone explain the advantage of using an Ubuntu Private Cloud for a school rather than the normal network setup?  My understanding is the Cloud allows you to save files "up there" and access anywhere, which would obviously be the same as the normal networked environment.

Cheers for anyone who can suggest genuine advantages for a school(!).

---

### Post by Rusty au Lait on 2010-10-07
Well, I am trying to think of any situation where a cloud would be the best or only form of user space/application. Nothing so far.
What is your current setup? Are you somehow restricted with computer access? One computer, many students? Students are all online? Thin clients?
An instance in the cloud can attach permanent storage and save data but every time the instance is terminated and restarted it starts from an original image.

---

### Post by kim0 on 2010-10-07
Well, different people mean different things by "cloud". And file storage is surely not the only thing. UEC enables you to provide an infrastructure where your customers/students are able to spin up virtual servers on demand, and be charged for the used time. Not sure if that use model applies in a school, but if it does then go ahead

UEC also provides cloud storage that is Amazon S3 compatible, however, if all you need is storage for students, then there are probably easier solutions to meet your need.

It's quite important that you mention exactly what you want to achieve, what would you use this cloud for exactly ?

---

### Post by webworldx on 2010-10-13
Thanks for the responses. I thought as much regarding the storage issue. I had hoped Cloud services would provide a better way in future to allow all to distribute and interact with applications / storage for pupils. A switch to thin clients in the future and the removal of licence fees for remote desktop apps etc would be welcomed in schools!!!

---

### Post by kim0 on 2010-10-13
Who needs licenses when you can run Ubuntu :)

---

### Post by graha1994 on 2010-10-14
Do we have to install Ubuntu Cloud client to download files from there?

---

### Post by Rusty au Lait on 2010-10-14
I do not think there is anything that can be called a client in the UEC world. There is an instance (a virtual machine of many flavors) that is accessible from anywhere on the internet. If the instance is a web server you can point your browser to it and upload/download files from it. If it is a linux host you can ssh to it and upload/download files.
An application that supports a school environment (e.g. teacher's aids, student administration, parent contact, testing, lesson plans, library) can access all the parties using the internet without the added complexity of UEC.
Hope this helps

---

