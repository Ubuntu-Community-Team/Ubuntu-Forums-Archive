---
title: "No Direct3D in HKCU&gt;Software&gt;Wine"
date: 2009-04-26
forum: Wine
---

### Post by Autocon on 2009-04-26
Hello!

This is my first time posting, so bear with me =)

I am currently using Wine 1.1.20, and the reason I am looking for the Direct3D Folder is so that I can add the key "DirectDrawRenderer" and "RenderTargetLockMode" with the value "readtex" so that I can hopefully solve the problem of Starcraft running slow. The issue with this, is that There is no Direct3D folder to create these keys into! 

So does anyone have any advice, as in to simply create the folder, or could it be in another location? I heard there is a spot inbetween versions of wine where they decided to remove that folder from HKCU

Any assistance would be greatly appreciated!

---

### Post by Namtabmai on 2009-04-26
You just need to create the folder/key if it doesn't already exist. :)

Double check you are looking in the right place thou.

---

### Post by Autocon on 2009-04-26
> **Namtabmai said:**
> You just need to create the folder/key if it doesn't already exist. :)

Double check you are looking in the right place thou.

I am definitely looking in the right place according to the Wine Wiki but upon further inspection I have found it in HKEY USERS. And one of the values was already set for me!

Now I'll put in the other key and update it and see whether that changes the playability of the game. And of course I will report back here for anyone else who has the same problem as I do.

Though, lets say I were to create a Direct3D Key in HKCU, would I have to specify a value for it to allow the other keys to work within that key? Or does it not have any effect on the other keys within?

Edit: When the Direct3D Key, along with the others, were created in HKCU, they were also created in HKEY USERS. So it wasn't that they were already there but in creating them, they were created in the other key line.

---

### Post by Namtabmai on 2009-04-26
I think I know the value you are trying to set, but it's been a few months since I fiddled with it.
The Direct3D is just a folder that will contain other keys/folders, so you can set a value for it only create it.

---

### Post by Autocon on 2009-04-26
> **Namtabmai said:**
> I think I know the value you are trying to set, but it's been a few months since I fiddled with it.
The Direct3D is just a folder that will contain other keys/folders, so you can set a value for it only create it.

I am assuming you meant that I do not need to set a value for it, but to just create it so that I can have the other folders/keys contained within? If so that is what I have done!

Unfortunately this had no effect on the operation of Starcraft =(

Any other suggestions?

---

### Post by Namtabmai on 2009-04-26
Yes I did mean that, apologies.

I'm afraid I don't play Starcraft so I'm not sure what other advice I can give. I assume you've read through the wine appdb entry,
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=51](http://appdb.winehq.org/objectManager.php?sClass=version&iId=51)
especially the comments from other users at the bottom?

---

### Post by Autocon on 2009-04-28
> **Namtabmai said:**
> Yes I did mean that, apologies.

I'm afraid I don't play Starcraft so I'm not sure what other advice I can give. I assume you've read through the wine appdb entry,
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=51](http://appdb.winehq.org/objectManager.php?sClass=version&iId=51)
especially the comments from other users at the bottom?

Well I thought I had looked through it all, but then I happened upon the thread about disabling 3-button emulation, and that did the trick! That and possibly because I decided to use Cedega a) because I am still somewhat GUI dependent and b) so I could verify that I had opengl operating, as well as fbo.

Either way, of those three I have it working flawlessly!!

Thank you for your assistance, it was MUCH appreciated! :)

---

