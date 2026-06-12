---
title: "lamp installed now what???"
date: 2009-02-08
forum: Server Platforms
---

### Post by jblinuser on 2009-02-08
ok so ive got a machine up and running with ubuntu server 8.10. i installed webmin, apache, mysql, and php5. the main reason i have put together a server is for media streaming and storage. at this point i am not sure what i need to use to stream music to my other computers. i am able to log into the server using webmin but what package do i need to stream media?

---

### Post by ken22 on 2009-02-08
vlc would do depending on the scale of what you're trying to do.

Doesn't need any of the stuff you've installed. 

If you throw a media file into the /var/www directory, you'll be able to serve it from [http://localhost](http://localhost)

---

### Post by punx45 on 2009-02-08
yeah depends on what devices you are serving to.   if its ps3 xbox type stuff, search for linux upnp server and you have a ton of choices.   or if you just want to play music on other computers, just share the drive, and use the software of your choice to play the music.   list goes on.

---

### Post by jblinuser on 2009-02-08
ok the way i have it setup right now is i have an external drive with the music on it connected to the server. it is mounted and i am able to view it through webmin. the problem is i dont know how to get it to stream to the computer that i am viewing it with. as far as putting it the /var/www im not quite sure how to do that since it is an external drive. i can go to [http://localhost](http://localhost) and see the test page that says "it works" but i dont know how to map the drive to that file.

---

### Post by punx45 on 2009-02-08
you want to stream it so that you can tune into it like a radio station on another computer?  or you just want the files available to other computers on the network?   and what are the other computers on the network?

---

### Post by jblinuser on 2009-02-08
yes i would like to be able to stream the music to another computer in the house or possibly on my xbox. we have a vista laptop, an ubuntu 8.10 laptop, and the xbox 360. now im not sure that streaming to the xbox is really important or even possible without a lot of hassle so thats not a big deal. but what i would like to be able to do is store music on the server and be able to access it from either of the laptops. i think that to be more specific i would like to be able to have it setup like rythembox or itunes where i can create a playlist or something like that and then click play and it will stream that audio to the client computer. that way all of our music or video can be stored in one central location and can be accessed for playback from the two main computers.

---

### Post by punx45 on 2009-02-08
in that case probably the easiest thing to do is set up a samba share.   then you can access the music on the other computers like you would if the music was stored locally on them.

---

