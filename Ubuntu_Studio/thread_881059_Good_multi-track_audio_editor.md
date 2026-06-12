---
title: "Good multi-track audio editor?"
date: 2008-08-05
forum: Ubuntu Studio
---

### Post by Kotjze on 2008-08-05
I've been looking for a good program that can play and edit multiple audio tracks at once (kind of like a simple version of [Acoustica Mixcraft](http://acoustica.com/mixcraft/) on Windows). I had a look at some in the Add/Remove thing, and Jokosher seems good, but whenever I click play, or try to save it as a single audio file, the program just crashes.

Or is there some simple thing I can run the Terminal that would merge audio files together? I have this thing, ogmmerge, but that just joins the files end-to-end, but what I need is something that will overlap the files. For example, if I was recording myself playing guitar and playing bass, but they were in separate files, but they are both the same length and synced up, I want to stick them together so I have one audio file where the two are mixed together.

I can't seem to find anything that will work.

---

### Post by Stochastic on 2008-08-05
**Jokosher** shows some promise but it still needs lots of work to make it stable.
**Audacity** is the beginner-friendly multi-track editor right now.
**Ardour** is the big guy on the block and is by far the most powerful and most stable.
**Ecasound** is a very flexible command line editor (there are many tutorials out there to show you basic wave editing with it).

There's also others around: Rosegarden, Wired, LMMS, Muse, etc...

---

### Post by ajgreeny on 2008-08-05
I think **audacity** will do what you want, though I am not quite certain.  With that you can import two or more files and then merge them easily, and even move each one forwards or backwards as well, then you can finally merge them into a single file of whatever output file type you wish, as long as you have the appropriate codecs, of course.

I have used it a lot for stage sound effects, to, for example add dog barking sounds, track 1, to people chatting, track 2, and then a door bell, track3, and more dog barking, track 4.  It's dead easy to use and in the repos.  have a look and give it a try.

---

### Post by Kotjze on 2008-08-05
Audacity sounds like it might be useful for mixing down multiple files. Is there any kind of command line script that would merge the files like that, or are there only scripts that join them end-to-end?

Edit: Oh it seems ecasound might be able to do that. Going to look.

Edit 2: Ecasound does what I want, and in command line. Thanks! :)

---

