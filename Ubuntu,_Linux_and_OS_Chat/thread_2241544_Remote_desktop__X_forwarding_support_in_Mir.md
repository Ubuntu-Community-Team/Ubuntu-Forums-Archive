---
title: "Remote desktop / X forwarding support in Mir?"
date: 2014-08-26
forum: Ubuntu, Linux and OS Chat
---

### Post by jhuber72 on 2014-08-26
I've googled around looking for more information on this but have not been able to find any direct answers from mir developers.  The most I've found is a phoronix article that briefly mentions that it still needs to be worked on.  My question - does anyone know what the plans are, or current status is for remote desktop support with mir?  Will there also be something similar to what we currently have with ssh X forwarding?  I am the computer guy for my extended family, and I'm thinking of moving them from Debian to Ubuntu in the near-ish future.  Once 16.04 comes out (if it does ship with mir as default) I would like to have a way to help them out via remote desktop if they run into any problems...hence my question above.________________Also...I can't seem to figure out how to do paragraph breaks in this forum :?

---

### Post by TheFu on 2014-08-27
X-forwarding over a WAN connection is painful. Nobody should do that.
Look at **x2go** for a solution based on the NX protocol which includes ssh tunnels.  It works well on 14.04 today, including remote audio.  Of course video is less than great, but I don't think any non-commercial solutions handle that very well.

---

### Post by grahammechanical on 2014-08-27
Up until now the Ubuntu developers have been concentrating on getting a Ubuntu phone/tablet image ready to be given to the phone/tablet OEMs for pre-installation on their mobile devices. Work has only just started on converging the phone/tablet code base into the desktop code base. It is too early to ask this kind of question.

MIr will replace Xserver. So in Ubuntu 16.04 it will not be possible to use X forwarding. But Mir is not going to be back ported to 14.04 and that has 5 years support starting in April 2014. Ubuntu 16.04 will need an alternative to X forwarding or many people like yourself will not install 16.04. And it is not desire for Ubuntu developers to shut out present Ubuntu users from future releases of Ubuntu.

There are a couple of places where you can keep up to date on convergence and even ask questions. On Ubuntu On Air every two weeks there is an Engineering team live hang-out. Various Ubuntu software engineers give updates on the work thier teams have been doing. We can ask questions by means of IRC. This was the most recent Engineering hang-out

[http://www.youtube.com/watch?v=NcbE_jgA9No&list=UUm7OifwnZoMCChidCJZQruQ](http://www.youtube.com/watch?v=NcbE_jgA9No&list=UUm7OifwnZoMCChidCJZQruQ)

And then there is the Ubuntu Online Summit with lots of sessions relating to the future development of Ubuntu. Again we can ask questions by means of IRC.

[http://summit.ubuntu.com/uos-1411/](http://summit.ubuntu.com/uos-1411/)

Another alternative would be to install the 16.04 development version when it becomes available in November 2015. Then you can experiment with the future 16.04 as it is brought to release standards over a 26 week period. You will have an opportunity at that time to file bug reports about this matter.

Some of us track the development branch of Ubuntu in the Ubuntu Development Version section of the forum.

Regards.

---

### Post by jhuber72 on 2014-08-27
Good replies, thanks.  I'll be keeping an eye on desktop-mir's progress.

---

