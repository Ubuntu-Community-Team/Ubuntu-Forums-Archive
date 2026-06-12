---
title: "Ubuntu desktop image"
date: 2016-07-16
forum: Virtualisation
---

### Post by yuri-weinstein on 2016-07-16
I am trying to find a latest ubuntu desktop RAW image that can be uploaded to dreamhost cloud, I see lots of server images, but no desktops.
Preferably with x11vnc and virtualbox installed and configured.

Does such a thing exist or I am pursuing the wrong path ?

Thx

---

### Post by DuckHook on 2016-07-17
I doubt such an image exists and though I wouldn't go so far as to call your path "wrong", it is irregular. Most cloud users are command-line for many reasons, not least of which are ease of use and security. On both fronts, the fastest and most secure way to communicate with a server image is through ssh. Your criteria imply that you want to remote desktop. The few who want to do so will likely install a full fledged DE on top of Ubuntu Server, then install a remote desktop server. Remote desktop technology are notorious security holes and one must really know what one is doing to harden them properly.

On the matter of VBox, you definitely are going down the wrong path. A VPS is already virtualised and one cannot nest vitualised images. You are allowed only one tier of virtualisation because VBox needs direct access to some parts of HW, which it won't have if already sandboxed inside a virtual environment.

---

### Post by DuckHook on 2016-07-17
*Thread moved to **Virtualisation** as the more appropriate forum to your issue.*

---

### Post by MAFoElffen on 2016-07-18
"DreamHost's" main service is web hosting. They do have a service they do called "DreamCloud," where they do cloud services. Is that would you mean?

Like DuckHook said, the prebuilt Ubuntu Cloud images (which the complete repos are: [HERE]("https://cloud-images.ubuntu.com/")) are all server images. Even if you look at the public page for clouds images by version, for 16.04 [HERE]("https://uec-images.ubuntu.com/releases/16.04/release/"), you can see that there are only server images.

Before I make a recommendation:
- What are you trying to do? What is your vision?
- What is your skill level with Linux (Specifically Ubuntu), 
- What is your experience with OpenStack, EC2 and on building EBS Boot AMIs?

Because if this is something where you are really going to need a desktop on a cloud image, then what I think it would take is start out with a UEC-ubuntu server image, customize, build, and publish a cloud image to how you want it--yourself.

EDIT-- Although, by-and-large, a GUI is not normally installed on a cloud image (because of the same security exploit risks DuckHook mentioned), I can see instances where it might be installed..

---

