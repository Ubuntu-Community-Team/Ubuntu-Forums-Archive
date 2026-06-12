---
title: "Gazelle Fails to Recover From Hibernation"
date: 2007-10-03
forum: System76 Support
---

### Post by arch_o_median on 2007-10-03
Hi all!   I'm a mostly happy Gazelle owner, but I haven't successfully recovered from Hibernation (or suspend) yet.
  
  I've tested two different possibilities:

  1)  the Nvidia graphics driver is attempting something called a "warm boot" which can be turned off in /etc/default/acpi-support

  2)  in the /etc/acpi/hibernate.sh:

 /sbin/s2disk -x "$xres" -y "$yres" $DEVICE

  the parameters passed here are problematic so I commented them out.

  
   Neither appeared to be the cause of "hibernationlessness".  

   What information should I post about my system to clarify the situation...   or is this problem solved already?     Am I the only one struggling with this?   
  Thanks for considering this!
--Josh

---

### Post by thomasaaron on 2007-10-03
What is the model number of your computer? (Go to the System 76 driver to find out.)

What desktop environment are you running?

What version of Ubuntu are you running? (Feisty?)

Did you try running the restore function on your System 76 driver? (I believe the suspend/hibernate fixes were worked into it.)

---

### Post by arch_o_median on 2007-10-03
Under "System information" in the System 76 Driver Installer the "System Model" is listed as "gazp3".   I assume that's the same as the number?

  I usually run wmii, but I'm running Gnome in order to access the GUI front for the System76 Driver.

  By looking in /etc/apt/sources.list I see that I'm checking things out of the "feisty" repositories, so I guess that means I'm running Feisty 7.04?

  I have now run the restore function.   

   Suspend (via the GUI) appears to work.  ( Tested once. )

   Suspend (via the keyboard) appears to work.  ( Tested once. )

  Now testing hibernate....

---

### Post by arch_o_median on 2007-10-03
Hibernate (via the GUI):

   1)  fades the screen
   2)  the hard drive light flashes
   3)  a black backgrounded gray box login screen appears

---

### Post by arch_o_median on 2007-10-03
Okay the restore function appears to have fixed suspend.  Thanks very much for the prompt and helpful tip.
  I'm still working on the hibernation issue....

---

### Post by arch_o_median on 2008-06-23
I'm now having difficulty with suspend/hibernate in Hardy 8.04.   I usually use the little moon (Fn->F1) to suspend.   I have not tried the "Restore System" option.  Thanks in advance!

---

### Post by arch_o_median on 2008-06-24
As suggested in the Daru thread on the suspend problem, it would be nice if there were some place I could check in on progress on this issue (suspend).  Of course, I'd like to offer any assistance I can.  I'd be happy to provide any diagnostics that might help!
   Does anyone else out there have a Gazelle Performance (gazp3) running Hardy that fails to recover from suspend?

---

### Post by arch_o_median on 2008-06-25
Hi all here're a couple of (naive) thoughts I've had about my suspend issues:

  1)  My uname -m shows:

0 /etc/default 527 $ uname -m
i686

   I believe that x86_64 might be a better result for my machine, but I don't know if this is likely to affect suspend

  2)  The output of dmesg contains errors related to "ata2" which I believe is my DVD player/burner.  Maybe there's a driver/kernel compatibility issue? I'd be happy to attach this output if would be helpful.
 
  3)  I've alternated between the proprietary and open source nvidia drivers...  perhaps a reinstall via the system76-driver would resolve driver conflicts and help with the suspend issue.  (I suspect not since others have similar issues and probably don't have these configurations.)

  My system76 driver tells me I have gazp3 (which is what I ordered) but the list of systems the system76 driver adds support for found here:
 [http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

  Doesn't include a silver gazp3.  My machine is in a silver case, is it nonetheless the same as "GAZP3 - 14.1 Black Gazelle Performance "?

  Thanks again for all the help, and please let me know if there's any information I can contribute!

---

### Post by arch_o_median on 2008-06-26
My /etc/default/acpi-support file had the following on line 10:

ACPI_SLEEP_MODE=mem

I suspended my machine using the Fn->F1 (moon) key-combination.

  When I used that key-combo to suspend I saw:
* shutting down alsa
* saving the system clock

then:
 screen blanked, then fan ran, and the leds turned off except for the power led which went to blinking green mode, fan shut-off, blinking led is only sign of life.

 So far, so good...  but when I attempted to awaken the machine (via key presses) the phenotype was:

  1) green light comes on and stays on
  2) fan begins running indefinitely 
  3) screen remains blank

   this state did not change until I toggled the power by pressing and holding the power switch.
  
  Again all of the above occurred when line 10 of /etc/default/acpi-support read:

ACPI_SLEEP_MODE=mem
 
I toggled line 10 of acpi-support from:

 ACPI_SLEEP_MODE=mem to ACPI_SLEEP_MODE=standby.

    I also ran system76-driver "restore-system".  (Stupid of me to change two variables between tests...)

  The above suspend-following-Fn->F1-key-press-combo changed.
  The:

* shutting down alsa
* saving the system clock

  shutdown diagnostics were the same, but then the fan came on and ran indefinitely...  that is, I never got to the everything off except blinking green LED stage!   

   So here's the interesting part.  When I restored line 10 to:
ACPI_SLEEP_MODE=mem
    And suspended as above, I get a new phenotype.   Specifically I get successful recovery!!!  :)
    
Moreover, when I powered up after the failed powerdown under the ACPI_SLEEP_MODE=standby experiment, I saw the nvidia graphics card splash screen.   This makes me think that my nvidia drivers/kernel configs were the source of my problem...   

   Okay, so one last thing I don't understand was that when I ran the system76-driver restore function and watched the apt-get install diagnostics I saw this:

"Reading state information... Done
nvidia-glx-new is already the newest version."
 
   So I'm guessing that I had that driver, but it wasn't the one being used?  and the restore function made it the "in use" driver?

   In any event, I really hope this helps someone.  Please let me know if there's any more info I can provide.
 
  I'm going to run some more tests.

---

