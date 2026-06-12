---
title: "Firewire setup in Lucid or Maverick 64bit"
date: 2010-12-18
forum: Ubuntu Studio
---

### Post by texla on 2010-12-18
Is there a trick to setting up Firewire in Ubuntu Studio Lucid or Maverick in 64 bit?

I have used studio successfully in Lucid 32 bit but with some xruns so I thought I'd try some other versions.  However I can't remember if there were some changes that need to be made to memlock or ubuntu studio controls to get going.  Also I think I read that it matters if the device is plugged in or not at startup.  Any other tips?

---

### Post by trulan on 2010-12-18
On Maverick - Don't run Ubuntu Studio Controls, and don't start up your computer with the device plugged in.  You may need to reconfigure jackd to enable memlocking and rt scheduling, if you did not select allowing these when jack was installed.  Other than that, it should just work.  Start the computer, plug in the firewire device, start Jack, and have fun!

On Lucid - exactly the opposite.  Do run Ubuntu Studio Controls and enable raw1394, do reboot your computer with the device plugged in.

---

### Post by texla on 2010-12-18
Cool - I'll try out Maverick again first - sounds simple enough!  I did choose the realtime Jack option during setup but I also had have the device plugged in at startup so maybe that change will be enough.... hope so - Thanks Trulan!

---

