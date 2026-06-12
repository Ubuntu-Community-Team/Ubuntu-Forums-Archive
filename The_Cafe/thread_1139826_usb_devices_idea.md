---
title: "usb devices idea"
date: 2009-04-27
forum: The Cafe
---

### Post by meeples on 2009-04-27
I've seen alot of talk in forums about the fact that you have to unmount usb storage devices for your changes to be stored on the device being a reason for alot of people not to use ubuntu or linux. I personally am used to it now and always unmount before taking my flash drives out but isn't  quite confusing for ex-windows users? 

so i propose that in nautilus there is a button for external storage devices called "save changes" or something to that effect that unmounts and remounts your device so you don't lose all your files when you take it out.

i think this would be a great feature to make using ubuntu alot easier for new users.

i know this is probably the wrong place to propose an idea but i just wanted to see what other people think?:P

---

### Post by meeples on 2009-04-27
anybody? :p lol

---

### Post by Tibuda on 2009-04-27
I don't think it is confusing for ex-Windows users.
I always thought 'unmount' in Linux was the same as 'safely remove' in Windows.

---

### Post by meeples on 2009-04-27
ye abut in windows if you remove ur device without safely removing it, you still have your files on the device, whereas in ubuntu you lose any changes you made.

---

### Post by Simian Man on 2009-04-27
I actually think it's much easier with Gnome since you just right-click on the device and select unmount.  On Windows you have to click on the "Safely Remove..." icon on the lower left and then try to remember which device letter yours is.

If you just pull your drive out on Windows, you also have a chance of losing data.

---

### Post by Tibuda on 2009-04-27
Didn't knew it. I always use 'safely remove' in Windows, so that's why I don't see any difference.
Thanks for the info.

---

### Post by Kareeser on 2009-04-27
I also believe that "unmount" is tantamount to "safely remove hardware" in Windows.

The point of this being that delayed writes to flash drives prolong the life of the drive in question.

Try Ubuntu Brainstorm... you'll get more responses there :) Link is in my signature.

---

### Post by meeples on 2009-04-27
> **Simian Man said:**
> I actually think it's much easier with Gnome since you just right-click on the device and select unmount.  On Windows you have to click on the "Safely Remove..." icon on the lower left and then try to remember which device letter yours is.

If you just pull your drive out on Windows, you also have a chance of losing data.

yea thats a good point actually. but ok forget about windows then, it's looking like the idea isnt very popular, but wouldnt it just be good in general if once you save files to a flash disk you could just click save changes so  you dont have to remember to unmount it before you take it out later?

---

### Post by Tibuda on 2009-04-27
> **meeples said:**
> yea thats a good point actually. but ok forget about windows then, it's looking like the idea isnt very popular, but wouldnt it just be good in general if once you save files to a flash disk you could just click save changes so  you dont have to remember to unmount it before you take it out later?

I agree. Maybe "remount".

---

### Post by meeples on 2009-04-27
> **danielrmt said:**
> I agree. Maybe "remount".

remount. yea i like that :)

---

### Post by JohnFH on 2009-04-27
Use the 'sync' command in the terminal for a one-off 'save changes' action.  If you want to shorten the lifespan of the usb drive as well as slowing it down then you can also specify the sync option in /etc/fstab, udev rule or hal rule so that your usb drive is automatically mounted with the sync option.

---

### Post by mxboy15u on 2009-04-27
I am not understanding the question here, I just tested this and when I insert a device, copy a file and just pull it out the file is still on the device. This is not the normal way it works?

---

### Post by JohnFH on 2009-04-27
> **mxboy15u said:**
> I am not understanding the question here, I just tested this and when I insert a device, copy a file and just pull it out the file is still on the device. This is not the normal way it works?

What mount options are used to mount the USB drive?  Post the output of:
```

mount | column -t

```

I have to say I've never encountered this myself, but then again, I always unmount the device.

---

### Post by Simian Man on 2009-04-27
If you don't unmount on either system, it is possible that your drive will have the files intact and it is possible that you will have data loss.  Basically it's playing Russian roulette, so always unmount cleanly.

---

### Post by mxboy15u on 2009-04-27
> **JohnFH said:**
> What mount options are used to mount the USB drive?  Post the output of:
```

mount | column -t

```

I have to say I've never encountered this myself, but then again, I always unmount the device.

I am not going to mess with it, but whatever options are the default are what I use.

---

### Post by meeples on 2009-04-27
see people are recklessly not unmounting there devices :P we need a button :popcorn:

---

### Post by mxboy15u on 2009-04-27
> **meeples said:**
> see people are recklessly not unmounting there devices :P we need a button :popcorn:

I have been living on the edge for as long as I can remember.

---

### Post by meeples on 2009-04-27
nobody i know actually unmounts things before taking them out the computer, we'd be saving flash drives across the world if we had a button ;)


think of the poor flash drives :P

---

### Post by mamamia88 on 2009-04-27
wait so if i save a text file and pull out the flash drive before unmounting all that work is lost?

---

### Post by meeples on 2009-04-27
> **mamamia88 said:**
> wait so if i save a text file and pull out the flash drive before unmounting all that work is lost?

as far as i can tell theres a risk, i think its more risky if you delete something from your flash drive and then just take it out becoz then computer hasnt been able to empty the recycling bin like it would if you unmounted. i think. :(

---

### Post by mamamia88 on 2009-04-27
> **meeples said:**
> as far as i can tell theres a risk, i think its more risky if you delete something from your flash drive and then just take it out becoz then computer hasnt been able to empty the recycling bin like it would if you unmounted. i think. :(

ok ill just remember that thanks for the warning

---

### Post by benj1 on 2009-04-27
the problem with these kinds of things is that they don't really solve the problem, its just displaced to when people use a different distro. redhat (i think) have had these kinds of discussions when they introduced a default -i flag for rm. i will agree though that users need to be made aware of these things maybe a short differences "between linux and windows" note would be helpful?

---

