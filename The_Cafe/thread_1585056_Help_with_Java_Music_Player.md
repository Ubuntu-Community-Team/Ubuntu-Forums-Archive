---
title: "Help with Java Music Player"
date: 2010-09-30
forum: The Cafe
---

### Post by chessnerd on 2010-09-30
Alright, I'm working with my college's radio station to make a new music player for them (so they don't have to pay a couple hundred bucks for professional software). So far, things have really been coming together and we only lack a couple of features. However, I was wondering if some of the more experienced coders here might know how to do a few things that have stumped my fellow coder and I...

1. We currently build a JAR on the main server (running CentOS), but we would like to have that JAR converted into a Windows EXE for several reasons. Is there a way to convert an executable JAR into a Windows EXE file in Linux? (Yes, I know this defeats the purpose of Java as a platform-independent language, but we use Windows-only libraries for CD ripping already.)

2. The player needs to stream audio to the station's website (which is run by the CentOS server). My partner says he has some idea about how to go about this, but says we will need to "do a lot of Googling." Is there an online guide about (or a library for) streaming audio in Java?

---

### Post by lykeion on 2010-09-30
1. Install4J was the first that came up in my mind, but you don't need an installer I guess, just a EXE wrapper? I haven't tried it myself but _[JSmooth]("http://jsmooth.sourceforge.net/")_ seems to be what you are looking for.
And here's a good article on the subject: [http://www.excelsior-usa.com/articles/java-to-exe.html](http://www.excelsior-usa.com/articles/java-to-exe.html)

2. The player needs to stream audio to the server? Shouldn't it be the other way around or am I misunderstanding something here?

---

### Post by chessnerd on 2010-09-30
Thank you for your reply.

1. I read that exact article when I looked up converting JARs to EXEs. Install4J would be fine if it was free (or even cheap). We've looked at JSmooth, but we have no idea how we would implement it. It says that it can run on any OS because it is written in Java, but when we downloaded the ZIP the only executables were for Windows and there was no Java program to compile. It is open-source, though, so I'll download the source and see what we can do with that...

2. The "player" is technically a player at both ends because the DJs want to be able to hear the music on their end while streaming it to the player on the website. I suppose that's not the best name for it, but that's what we've been calling it. It functions as a simple player, but it needs to be able to connect its audio output to the player on the website being hosted by the server.

---

### Post by lykeion on 2010-10-01
[http://stackoverflow.com/questions/2011664/compiling-a-java-program-into-an-exe](http://stackoverflow.com/questions/2011664/compiling-a-java-program-into-an-exe)

[http://www.oracle.com/technetwork/java/javase/documentation/index-135173.html](http://www.oracle.com/technetwork/java/javase/documentation/index-135173.html)

---

