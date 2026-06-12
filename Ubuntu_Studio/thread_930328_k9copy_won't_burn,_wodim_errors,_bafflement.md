---
title: "k9copy won't burn, wodim errors, bafflement"
date: 2008-09-25
forum: Ubuntu Studio
---

### Post by skullmunky on 2008-09-25
Ok, here's a weird one.

When k9copy gets to the burning stage, I put in a blank DVD and it says that, according to wodim, there is no space on the disc.  More detailed error output:

```

An error occured while Burning DVD: wodim: Bad Option: tsize=genisoimage:.
Usage: wodim [options] track1...trackn
Use wodim -help
to get a list of valid options.
Use wodim blank=help
to get a list of valid blanking options.
Use wodim dev=b,t,l driveropts=help -checkdrive
to get a list of drive specific options.
Use wodim dev=help
to get a list of possible SCSI transport specifiers.
Insert an other DVD

```

It's strange, this app's been working great for me for years and then suddenly got all confused.  

I *did* get a new DVD burner, could that be why?

When I burn the DVD using K3B, using the files in /tmp that k9copy created, it works fine.

When I set k9copy to use K3B, which it used to do, it crashes my X session and returns to the login screen when it gets to the burning stage. 

Baffling!

EDIT: When I insert an empty DVD, and I get the "What do you want to do ... " dialog and choose "Data DVD with K3B", my X session crashes. But if I launch K3B and then burn the disc, everything is fine.

So that explains why it's dying when launched from k9copy - it's not k9copy's fault.

---

