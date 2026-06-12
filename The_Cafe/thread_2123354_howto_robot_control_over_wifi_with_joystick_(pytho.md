---
title: "howto robot control over wifi with joystick (python? shell? pipes? ssh? telnet?))"
date: 2013-03-07
forum: The Cafe
---

### Post by Frankels on 2013-03-07
Hi, I need some advice so I don't get lost in a jungle of overcomplicated programming. The problem I'm facing is the following: I have a robot (more like a stack of parts and an old PC) to which i can connect over wifi. it has linuxcnc on it. I can start linuxCNC remotely with ssh and then I can use telnet to pipe commands from a script into linuxcncrsh: telnet 192.168.1.75 5007 <./scriptforlinuxcncrsh. This lets me -at this early stage- start, jog and stop a steppermotor. So far so good. I also have a sidewinder joystick which i want to use to ultimately steer the robot and maybe control a robot arm on the robot (i can see the joysticks output with jstest on /dev/input/js0). This doesn't necessarily need to go via linuxCNC, it can also go low level by commanding the parallel port for instance.

Now I'm trying different configurations of software controlling the hardware over wifi, but it's hard for me to figure out what the best way is to go about things: For instance: 
I could have a number of shell scriptscontrolling linuxcnc on the robot that I call remotely with ssh when a python script reads certain movements on the joystick. Or i could pipe python scripts into telnet over ssh... or... anyway I'm getting confused. 

What would be the most organised (safe?) yet not too complicated way to go about this? I don't want to reinvent the wheel, and I feel like that's exactly what I'm doing when I'm piping telnet commands over ssh... (that's not exactly what I'm doing-  just illustrating my confusion)
I posted this in cafe 'cause this doesn't really fit a category (suggestions?)

hope you guy's can help

---

