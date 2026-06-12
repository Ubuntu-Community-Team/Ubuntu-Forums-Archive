---
title: "Vbox Guests do not get cpu time from the Host"
date: 2017-03-26
forum: Virtualisation
---

### Post by lammert-nijhof on 2017-03-26
Up to yesterday I used my desktop as Vbox host. On that HP dc5850 (3 core Phenom with 4 GB of RAM) the memory became a scarce resource. And getting XP, Vista or e.g Mint to run even as a single VM was a challenge. The combination of host and desktop did not seem a very good combination. Installing Peppermint a sexy mix of Lubuntu and Mint on a Pentium 4 processor for the children, did give me an idea. Peppermint was only using between 200 - 250 MB and Ubuntu 16.04 went over 1 GB. I did that job on Saturday, installed Peppermint 7 on a free partition and Virtualbox from the repository. I was very happy I could load Mint, XP and Ubuntu 10.04 or Vista with e.g Mint at the same time and things were relatively responsive also the host itself. 

I installed tvtime on the host, because I expected tvtime to need the real HW. No sound. Starting to look at the sound I detected that sound became a stuttering disaster as soon as a VM was loaded. That was true for both, music played on the Host Peppermint 7 and music played on the Guest e.g. XP. OK a sound problem, so I started to look at pulse audio and ALSA issues and found a suggestion from a knowledgeable person to change the behavior of the Intel HDA driver from timer driven to the old interrupt driven way. That solved the problem at the cost of a small distortion, almost neglectable on the XP Guest and more disturbing on the Vista Guest. OK I decided to bin the problem for the moment and to move on.

Then I noticed that the XP task manager and the ASC performance monitor both stopped for some times seconds, the graphs did not move and percentages remained the same. The timing seemed comparable with my sound problem, where the sound also sometimes was bad or missing for seconds. It looks that Peppermint does not recognize that the VBOX guests needed CPU time too, they were starved for many seconds in a row. When I moved the cursor or when I started to use that interrupt driven ALSA driver to play music, the graphs of both system monitors/Task Managers moved on.

It looks that the scheduler of Peppermint is almost completely interrupt driven, no interrupts no 'ready' processes detected. Probably a good idea for an old Desktop PC. In Ubuntu 16.04 the scheduler also starts its work on a short timer. I started to look at parameters like sched_latency_ns and a few others, but upto now they were the same in Ubuntu and Peppermint. 

And now my QUESTION: Which scheduler parameter(s) do cause this difference in behavior? And what do I have to change?

I'm not looking for the next solutions:
[LIST]
[*]Buy more memory and use Ubuntu, I will buy more memory soon. But I live in the Dominican Republic and transport costs are 10 times the cost of that DDR2 memory, so as a pensioner I wait for my visit to Europe in the next 1-2 months.
[*]Try Lubuntu or another distro. Probably I will try Lubuntu or Xubuntu, if I cannot find a solution in Peppermint.
[*]Use the Ubuntu server. I hate the command line, I did have to live with it from 1969 till say 1993. I've seen enough of that on Philips and Digital computers, I really like that splendid progress called a GUI. Basically the server is my last resort, but I will install the Lubuntu or Peppermint desktop on it
[/LIST]

---

### Post by lammert-nijhof on 2017-03-26
Update: I have saved the peppermint installation on a diskimage and tried the same with Lubuntu. Same problem, all non external interrupt driven processes are not recognized by the scheduler of Lubuntu, so the VM guest is starved of cpu-time. To the people from Lubuntu and Peppermint I would say, take virtualbox out of your Apps Store, because it does not really work. Try Xubuntu next, I used it for some time as my main distro around 2011. Probably it worked at that time with virtualbox.

---

### Post by lammert-nijhof on 2017-03-27
Xubuntu, even its 2nd version of the release did not install without switching off ACPI in the bios. During the install another error occurred and I was left with a PC without a boot loader. My CD with boot repair was 32 bits, so I had to wait for the download of the Ubuntu Server through my laptop. I skipped Xubuntu, it seems too unreliable. The Ubuntu server performs better, but it has basically the same problem. The graphs of the system monitor / task monitor are moving along, but from time to time it is somewhat irregular, resulting in terrible stuttering sound for the music. It has not been lost time, because I realized it had KVM as an installation option. Basically I'm looking for a one computer desktop solution, but it would be interesting to try KVM, it surely will be able to start VMs. Again with a Lubuntu desktop,I could also use it locally,if needed through rdp or vnc.
I am stuck with Ubuntu, the master itself. I will try to trim it with respect to memory usage and optimize it completely as a VM Host, maybe also by using the Lubuntu desktop instead of the Ubuntu desktop.

Again, if I could tune the scheduler of Peppermint 7, that would be my preferred solution.

---

### Post by lammert-nijhof on 2017-03-27
OK problem solved. Everything works as expected. The solution with the Lubutu desktop on top of the Ubuntu installation did not work. Again the VM Guest were starved of cpu time and the system monitor graph did not move and the music was a complete disaster. The master Ubuntu itself did the job, after being slimmed down to around to 375 MB. With Lubuntu/Peppermint it would have been 100-150 MB less, but it simply did not work. Probably something in the desktop makes the system behave as it does, but I have no clue, how that has been achieved. Maybe the desktops do set some parameters for the scheduler. I'm now going to transfer my current desktop to a VM, but first I try it out with the 17.04 beta. I'm a happy person, I can play around without rebooting all the time. I just use 4 Unity desktops and the desktop switcher to move between the running OSes.

Long live Ubuntu!! The best distro of all, the papa distro beats its children.

---

