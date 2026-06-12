---
title: "Getting the most out of my GazP7"
date: 2012-07-28
forum: System76 Support
---

### Post by imnotanerd on 2012-07-28
How can I get the most out of my new GazP7? It has the base i7 offered and I bumped it up to 8 gigs of ram. But being an i7, it's a **HUGE** bump for me as I come from a dual core pentium processor. But I noticed, I am playing a java based game, and watching a dvd at the same time. The java game slows down tremendously, even at mid settings. The game by itself is laggy even when the dvd isn't playing. The i7 has the HD 4000, which is supposed to be a huge improvement over HD 3000. I already installed the System76 Driver's off the setting's program. How can I make this the i7 it was meant to be?

Edit: How can I upgrade which version of ubuntu I'm running? When I go to edit my profile, I get a notice saying I need 50+ posts.

---

### Post by jakobcreutzfeldt on 2012-07-28
Consider installing libva-intel-vaapi-driver (available in the software repositories) and a video player which supports VAAPI hardware video acceleration, such as VLC or MPlayer. This should improve performance while watching video.

As for the Java game, it's difficult to say. Is it 2D or 3D? Does it give you any options to tweak for performance? Open up System Monitor while the game is running. Is the CPU usage very high, or at least higher than you would expect when there isn't much going on in the game? It could be that the game is doing all the graphical rendering on the CPU and not the GPU. If that's the case, you'll have to figure out how to get it to use hardware graphics acceleration.

In truth, the HD 4000 graphics chip is seriously impressive. My gazp7 has the i7 3820QM CPU, and with it and the integrated graphics, I have been able to run Amnesia: The Dark Descent at full 1920x1080 resolution, with all but one of the graphical options set to their maximum and it runs like a dream. Some of that may be due to the higher-power CPU but much of it is thanks to the HD 4000 GPU. (note that I have gotten better graphics performance in Arch Linux in which I have the latest Intel xorg drivers, but in Ubuntu it's still very respectable).

Lastly, just make sure that you don't have a ton of stuff running in the background. With that CPU it shouldn't matter much, but it's worth noting anyway. Whenever I play games, even with this monster of a CPU, I still minimize the amount of things running in the background.

---

### Post by imnotanerd on 2012-07-28
I've installed it, and it runs fine now. But the game itself, I've put in all mid graphics settings (it's a 3D game) and it's still a bit slow. Here's a screenshot of the system monitor. [IMG]http://img.ly/system/uploads/005/086/687/original_Untitled.png[/IMG]

---

### Post by jakobcreutzfeldt on 2012-07-28
To me, that CPU usage looks pretty high if not much was going on in the game at that moment, though it's really hard to say for sure. It's *possible* (though not certain) that it's using the CPU for rendering somehow. I have no idea. 
I would recommend searching around on the internet for other Linux users talking about that game. Perhaps some others have experience in tuning it for the best performance. Sorry I can't help more in that regard.

---

### Post by imnotanerd on 2012-07-28
Chrome was the only thing running with one tab for the game when that screenshot was taken. Well, thank you for your help!

---

### Post by philbert on 2012-08-01
> **imnotanerd said:**
> Chrome was the only thing running with one tab for the game when that screenshot was taken. Well, thank you for your help!

There is something you may want to try for the Java game: Increase the amount of memory Java allocates to the java heap in that game. 

32 bit JVM's used to default to 128M for a beginning maximum heap size  - the Xms value - and a  hard limit of 256M for the maximun heap size f- the -Xmx value - or an application. That may still be the case with 64 bit JVM's also. 

What would happen is that, although Java runs its own garbage collection, it does not do so until the memory usage approaches the current  heap size, Java will then allocate more memory for the javaheap in increments, and run garbage collection when it approaches the new limit  until it reaches the final maximum size. Once the actual memory usage approaches the maximum heap size there will be considerable CPU cycles consumed as the JVM increasingly runs garbage collection. 


Determine how the game is being launched. at some point  a java ..javaoptions string in the command is being invoked. You will want to insert a JVM argument  -Xmx512M for 512M of memory or if an -Xmx argument is already being passed, then increase its value.

Note that this is completely unrelated to the DVD being played unless the JVM is so busy running garbage collection, it is contending for CPU time that the DVD player is taking, That would be a real stretch but since there have been no recent suggestions, it may be worth a try.

---

### Post by Ubun2to on 2012-08-02
Off topic, but how did you get Java working?
OpenJDK works like a charm, but trying to use the Java from Oracle's website is something I can't figure out how to do.

---

### Post by philbert on 2012-08-02
> **Ubun2to said:**
> Off topic, but how did you get Java working?
OpenJDK works like a charm, but trying to use the Java from Oracle's website is something I can't figure out how to do.

I created a directory in /usr/local named java, downloaded the .bin into there.  
I then prepended PATH in .profile with the directory of both the jdk/bin and the jre/bin

so when I run java -version I  get the Oracle version to launch and respond.
Java(TM) SE Runtime Environment (build 1.7.0_05-b06)
Java HotSpot(TM) 64-Bit Server VM (build 23.1-b03, mixed mode)
And I get a similiar result for javac.
Now the  Eclipse Juno installed can use the Oracle version instead of the Iced Tea version.

Interestingly, I first tried extracting into /usr/java  which is my standard location on other Linux platforms and could never get it to work from there. I never did figure it out.

---

### Post by Ubun2to on 2012-08-03
> **philbert said:**
> I created a directory in /usr/local named java, downloaded the .bin into there.  
I then prepended PATH in .profile with the directory of both the jdk/bin and the jre/bin

so when I run java -version I  get the Oracle version to launch and respond.
Java(TM) SE Runtime Environment (build 1.7.0_05-b06)
Java HotSpot(TM) 64-Bit Server VM (build 23.1-b03, mixed mode)
And I get a similiar result for javac.
Now the  Eclipse Juno installed can use the Oracle version instead of the Iced Tea version.

Interestingly, I first tried extracting into /usr/java  which is my standard location on other Linux platforms and could never get it to work from there. I never did figure it out.

Will try that when I get the chance.
I just wish Oracle would make .DEB packages.

---

### Post by philbert on 2012-08-03
> **Ubun2to said:**
> Will try that when I get the chance.
I just wish Oracle would make .DEB packages.

The problem with using rpm or deb is that I don't know what is going where. So even on RedHat Systems, I use the .BIN version. Once I drop the .BIN in that directory, It's a matter of making the binary executable using chmod a+x and then ./the .bin file which is a self extracting file that unzips the contents in a directory within the java directory.

I apologize if I am being circumspect in my descriptions of what to do. But I am trying to conform with the forum rules as I understand it  against supplying complete syntax to shell commands.

---

### Post by isantop on 2012-08-03
> **philbert said:**
> The problem with using rpm or deb is that I don't know what is going where. So even on RedHat Systems, I use the .BIN version. Once I drop the .BIN in that directory, It's a matter of making the binary executable using chmod a+x and then ./the .bin file which is a self extracting file that unzips the contents in a directory within the java directory.

I apologize if I am being circumspect in my descriptions of what to do. But I am trying to conform with the forum rules as I understand it  against supplying complete syntax to shell commands.

The DPKG database will contain a listing of all files installed by a deb package, and you can even extract a .deb and look at its contents that way. You don't have *control* over where the files go, but you can definitely *find out* where they went/will go.

---

### Post by philbert on 2012-08-03
> **isantop said:**
> The DPKG database will contain a listing of all files installed by a deb package, and you can even extract a .deb and look at its contents that way. You don't have *control* over where the files go, but you can definitely *find out* where they went/will go.

Thanks isantop,
It's something I will need to investigate further.

---

