---
title: "how do I setup xrandr??"
date: 2015-12-26
forum: Virtualisation
---

### Post by lance12 on 2015-12-26
So I'v posted here before and got help from T.J. about getting a kvm windows system running using qemu. when I did that setup I only had one monitor so switching inputs was how I viewed my windows, but now I have a second monitor and I would like to use both monitors for linux until I start my kvm guest. from what I've seen and read I need to use xrandr to do this but xrandr doesn't see my monitor that is plugged into the guest passthrough graphics card. So I was wondering if anyone had any idea of what I need to do. 

my setup so far is:
-radeon hd 6670/7670 (for the host debian- plugged into screen 1)
-nvidia gtx 970 (for the guest windows 7-plugged into screen 2) {claimed by vfio-pci on boot}
-mouse/keboard = synergy

so using the xrandr command It sees screen 1 which is plugged into the radeon but it doesn't see screen 2 which is plugged into the 970. am I doing something wrong?

let me know what other info I need to post if any, and thanks in advance.

---

### Post by TheFu on 2015-12-26
basically, you have 2 completely separate computers using 2 completely separate video cards.  Don't think xrandr (or X/Windows) will help with that in any way.) so long as you have setup GPU passthru.

---

### Post by lance12 on 2015-12-29
[https://www.youtube.com/watch?v=37D2bRsthfI](https://www.youtube.com/watch?v=37D2bRsthfI)

this is an example of what I want to do, in the description it says he's using xrandr to do it. so it is possible I'm just not sure how.

---

### Post by brian-mccumber on 2015-12-29
In the description the author noted that you must have a > [FONT=Roboto][COLOR=#333333]Please note that you'll need both a VT-d capable CPU and mainboard(or the AMD equivalent). And of course, 2 gpus, for example 1 dedicated PCIe card and the onboard gpu of a core i* processor.[/COLOR][/FONT]

[COLOR=#333333][FONT=Roboto]And also he has two connections to the left monitor from both gpu's so both operating systems can utilize it, from your post it looks like you have the monitor that is supposed to switch back and forth hooked up to only one gpu.[/FONT]

[FONT=Roboto]So I'm thinking you don't have the hardware hooked up correctly for this and/or your hardware will not support this. VT-d looks like it's Intel proprietary hardware so your cpu and mb will probably have to be Intel or Intel compatible/equivalent. [/FONT][/COLOR]

---

### Post by lance12 on 2015-12-29
I have the kvm guest running fine, I was just trying to set up the monitors for my host to use both before the guest is on. but I think your right that he has cables from both gpus going to the main one, so hes probably using a hdmi splitter of some sort.

---

### Post by brian-mccumber on 2015-12-29
He's not using a splitter he is using the hdmi port and the dvi-i ports on the switchable monitor connected to both gpu's. He is using the dvi-d port from the onboard gpu to the static monitor. If you're using older monitors it may only have one port so you will need a monitor with at least two ports that match two ports on one of the gpu's.

> 
[COLOR=#333333][FONT=Roboto]- GPU 1: Onboard Intel HD Graphics 4600 (i915), HDMI connected to left monitor, DVI-D connected to right monitor[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]- GPU 2: Gigabyte Windforce GTX 770, DVI-I connected to left monitor
[/FONT][/COLOR]

---

### Post by lance12 on 2015-12-29
but in order to have both of those cables plugged into the tv and switch between them **without** switching the inputs on the screen its self he would have to be using a splitter, so if he's not using a splitter then how is he doing the switching?

---

### Post by brian-mccumber on 2015-12-29
> 
[COLOR=#333333][FONT=Roboto]Whenever I feel like playing Windows games I disable the left monitor using xrandr and start qemu which uses the passed-through pcie gpu as vga.
[/FONT][/COLOR][COLOR=#333333]

[FONT=Roboto]I am not trying to be mean but I keep quoting this article to answer your questions. Maybe you need to go back and read it slower if that doesn't work try to contact the guy who made this tutorial.[/FONT]

[FONT=Roboto]It doesn't look like he is using a kvm switch just the software from what I read under the hardware and software sections of this guide. It doesn't mention anything about kvm switches so maybe that is where your problem lies. He is also not using two computers he is running Windows in a VM on the Ubuntu machine. It even says that in the title of the article - [/FONT][/COLOR][h=1]Qemu/KVM + vfio = Virtual machine for gaming[/h]

---

### Post by lance12 on 2015-12-29
I know what hes doing with the virtual machine, I already have a running one. my question, which was a simple one, is how is he using the left monitor in the video with 2 inputs with out switching to the second input. correct me if I'm wrong here but if I had and xbox and ps4 plugged into a tv in to separate inputs then in order to view the xbox i would have to be on the xbox in put. then if I wanted to view I would have to ***_switch to the second input using the_******_ monitors remote or button._*** this is the same for what he is doing. he has 2 card plugged into 1 monitor, so they either have to be on separate inputs which is what you are telling me, or they have to be on input using a splitter. if they are on seprate inputs going into the monitor then why doesn't he have to switch inputs on the tv? in the description he says hes using xrandr to do this.
 >  [COLOR=#333333][FONT=Roboto]Whenever I feel like playing Windows games I disable the left monitor using xrandr and start qemu which uses the passed-through pcie gpu as vga.[/FONT][/COLOR]  

so i ask again, do i need a splitter to do what he is doing or do you still think he is using separate inputs into the monitor without switching between them.

---

### Post by brian-mccumber on 2015-12-29
> [COLOR=#333333][FONT=Roboto]*I disable the left monitor using xrandr*[/FONT][/COLOR]

It looks like he disables the monitor using xrandr and then the vm uses that gpu and monitor exclusively when everything is set up correctly.

Also he is using monitors and not televisions so there is no input selection needed like there is on a television. Computer monitors will display whatever is being sent to them through any port without having to switch inputs.

---

### Post by brian-mccumber on 2015-12-29
If you insist on using the television as a monitor then you will have to manually switch your inputs using the remote everytime you make this switch.

---

### Post by lance12 on 2015-12-29
ok so now that we are on the same page mostly, the last thing you said is interesting. I have not owned a monitor with more than one input on it so I was not aware that they would automatically switch like that. I have an all tv setup so switching inputs is a necessity. would using a splitter so that an hdmi coming from my guest gpu and my host gpu are going into the same input on my tv work? then i would just have to us xrandr to turn off that screen before windows starts right?

---

### Post by brian-mccumber on 2015-12-29
Yeah sorry about the confusion, I was assuming you were using monitors but we are good to go now. If you use the television then you shouldn't have to disable the screen just switch to the input you use for the vm.

Back to the monitor television thing, I have a vga and a dvi port on my monitor and my graphics card. I can put both cables on and then connect either one to the monitor and it will display without me having to switch any inputs but it will only accept one input at a time tho so that is why he is disabling the screen. He is not disabling the monitor just the screen that his OS is using on that monitor so the other OS can claim it. If you're using a television that will accept more than one input then you should only have to switch inputs just like switching from cable to a dvd player.

---

### Post by lance12 on 2015-12-29
That is what I've been doing and it kinda sucks after doing it for a while. Its not a huge issue its just something I was looking into working on. I was wondering if I could work around the need to switch between inputs at all. I've never used a splitter so I was wondering if anyone on the forum has or had any other advise. sorry for the confusion as well, I was not aware that multi-input monitors automatically selected inputs like that. which explains how it works for his setup. do you think anything bad could happen if I tried to use a splitter?

---

### Post by brian-mccumber on 2015-12-29
I don't know for sure but I like experiments anyway so a splitter could possibly work but you would have to disable the screen so there are not two signals being passed to the same input port on the television.

As for having to switch inputs being a pain, I don't see how this is much different from switching inputs from watching cable tv to say an xbox or something. At least it is working right.

So has this actually increased your game performance for your Windows games run in the vm? It seems to me that having Windows on one drive and Ubuntu on another would still be better performance because there will be more ram and cpu available if Windows was running by itself. But if you're running at least a quad core with 64bit system using 16 gigs of ram and two different gpus, I don't see that there would be any performance issues at all.

---

### Post by lance12 on 2015-12-29
I'll test the switch tomorrow so I'll let you know how that goes. as for the switching goes I don't have anything else beside my pc so I only do the switching inputs for my vm.

as for the windows vm thing. I get around 96-98% performance compared to a normal windows install so not having to reboot for dual boot or trying to use wine is a blessing. plus with it only being a 2-4% loss its not even noticeable with my hardware, I could easily overclock and get that performance back XD

---

### Post by TheFu on 2015-12-29
> **lance12 said:**
> but in order to have both of those cables plugged into the tv and switch between them **without** switching the inputs on the screen its self he would have to be using a splitter, so if he's not using a splitter then how is he doing the switching?

My monitors auto-switch to the active input. When Windows is shutdown, that input isn't active, so the 2nd input from the onboard GPU (IGP?) is used.  When in Linux mode, the left monitor isn't using the fancy $450 GPU, it is using the onboard stuff, just over a different input to the monitor. The onboard Intel GPUs can drive 3 different monitors - sorta like how a laptop can drive 2 monitors (VGA + HDMI) - that's how my laptop drives dual monitors here.

No HDMI or KVM switch needed. It is purely the function of the monitor to pick the order of active inputs to be used and to make sure that the GPU dedicated to Windows comes before the Linux GPU (which is pushing 2 monitors).  BTW, I have a similar setup, just without the passthru stuff using a KVM switch and HDMI splitter+switch.

Make sense? 

I could be wrong, but don't think I am.

---

### Post by TheFu on 2015-12-29
Sorry - last post was pushed before I'd read the last 5-10 posts .... 

I have both HDMI splitters and HDMI switches (among other video and audio signal processing thingys) - I think you want an HDMI switch, not a splitter. Most will autoswitch to the active input for you. The only issues I've had was with HDCP crap getting in the way and no signal being sent to the monitor(s).

Remember - there are 2 video cards.
1 port on the Windows dedicated GPU goes to the TV on the left.
Port A on the Linux GPU goes to the TV on the right and Port B on the Linux GPU goes to the TV on the left.

Assuming all HDMI inputs here (which probably isn't a good assumption), a 2 port HDMI switch is all you need and only for the left TV.

---

### Post by lance12 on 2015-12-29
thanks for the advice, I'll definitely try to find an autoswitch to test as well. thanks for all of the help guys :)

---

### Post by heiko_s on 2015-12-30
I think the description underneath the video is quite clear. He drives 2 screens using the IGP and Xinerama, then switches the left screen to use a different input (from 2nd GPU) when he runs Windows, at the end he switches the screen back to the first input (IGP).

Have a look at the script that he posted in one of the comments under the video: [http://pastebin.com/rcnUZCv7]("http://pastebin.com/rcnUZCv7").

---

### Post by lance12 on 2015-12-31
if you've read the posts you would see that we came to that conclusion already. at first I was confuse because I didn't know that regular monitors auto-switched between inputs. after realizing that it was apparent what he was doing. unfortunately I don't have an auto-switching monitor so I'm looking for ways around. but that script is interesting and will probably come in handy :)

---

