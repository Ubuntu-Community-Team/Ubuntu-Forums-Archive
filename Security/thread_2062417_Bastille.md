---
title: "Bastille"
date: 2012-09-24
forum: Security
---

### Post by UltimateCat on 2012-09-24
I looked up machine hardening and security and found out about Bastille.
[http://bastille-linux.sourceforge.net/](http://bastille-linux.sourceforge.net/)

I checked my Synaptic Package Manager and the application is not in there.
So it appears that I can download it from here:
[http://bastille-linux.sourceforge.net/running_bastille_on.htm](http://bastille-linux.sourceforge.net/running_bastille_on.htm)

The instructions are a bit much for me.
```


[LIST]
[*]First, install the [Bastille RPM]("http://prdownloads.sourceforge.net/bastille-linux/Bastille-3.2.1-0.1.noarch.rpm?download"), like so:        
               rpm -ivh Bastille-3.2.1-0.1.noarch.rpm           
[*]Second, if you want to use Hardening mode, you'll need to install perl-Tk 
    (for our Graphical Interface) or perl-Curses (for console/text mode). 
    [COLOR=red](Installing perl-Tk/perl-Curses isn't necessary in Assessment mode, as it 
    generates a report in both HTML and Text.)[/COLOR]      You can usually do this most easily by getting the RPM shown in [this table]("http://bastille-linux.sourceforge.net/perl_rpm_chart.htm"), installing
      it via this command: 
      
             rpm -ivh perl-Tk-a.b-c.i386.rpm or         rpm -ivh perl-Curses-d.e-f.i386.rpm       Alternatively, you can install these using the CPAN method, [described here]("http://bastille-linux.sourceforge.net/perl_modules_cpan.htm"). 
      
 
[*]Third, run the bastille command:        
               bastille -x     (for Graphical Mode Hardening) or         bastille -c     (for Text Mode Hardening) or         bastille --report       (for [Assessment]("http://bastille-linux.sourceforge.net/assessment.htm") and Reporting)           
[*] **NOTE:** [COLOR=red]Just because you're su-ing or ssh-ing into a system doesn't mean you're stuck in text mode.[/COLOR] 
    You can use graphical (X) programs like Bastille's Tk interface or  browsers by forwarding your X connections over the ssh connection. It's  very, very simple. Just do this:      
        ssh -X root@remote_box   (when you were already SSH-ing) OR    ssh -X root@127.0.0.1    (when you would normally just su)
[/LIST]

```
Do I follow the terminal instructions or do I go to the Debian site?

Any advice would be a great help as I'm not sure how to proceed.

---

### Post by oldos2er on 2012-09-25
Get the deb file from [http://packages.debian.org/sid/all/bastille/download](http://packages.debian.org/sid/all/bastille/download)
You should then be able to double-click it and install it with Software Center.

---

### Post by UltimateCat on 2012-09-26
> **oldos2er said:**
> Get the deb file from [http://packages.debian.org/sid/all/bastille/download](http://packages.debian.org/sid/all/bastille/download)
You should then be able to double-click it and install it with Software Center.

Thank You!:)

---

### Post by oldos2er on 2012-09-26
You're welcome. If your problem is solved, please mark the thread as 'Solved' under Thread Tools.

---

