---
title: "How do you remove UbuntuOne and all other stuff that was installed?"
date: 2009-07-03
forum: Ubuntu One (CLOSED)
---

### Post by Oceanwatcher on 2009-07-03
If you use anything else than Ubuntu, beware.

This goes for Kubuntu especially. UbuntuOne is ONLY for Ubuntu! There is no KDE version available.

On the installation page, they have a button where it says "Install PPA". I would put it as strong as this: It is a lie!

They use it to install the whole package, including stuff you never asked for, do not need and most likely do not want. And they do not tell you about it either.

When a button say "Install PPA" that is exactly what it should do.

In my case it installed a lot of software. I did not ask it to do that. All I wanted was the PPA. The software would be fine to search for after this.

At this point I am pretty furious. This installation has littered my system with a bunch of Gnome stuff I really am trying to stay away from. My computer is running very well at the moment, and I want to be in full control of what is being installed on it. If I see a program demanding a lot of Gnome libraries, I cancel the installation.

In this case, the installation was done with absolutelyno information about what was being installed. And even worse, done under the pretence of installing a PPA.

Dishonest and not worthy Canonical. This is more the kind of tactics I am used to from Redmond...

Right now I am looking for a way to find out exactly what was installed so I can clean out the litter from my system. Do anyone have a list of packages and dependencies? Or a way to find out? Is there a log somewhere that shows what files went in?

---

### Post by zekopeko on 2009-07-03
Oh no!!! An application installed LIBRARIES that ubuntu client uses to function!!! what will i do?! all does python thingies are littering my system! and if i try really hard i can find the on my system consuming a couple of MB of space!!! Oh what will i do? I know. I'm gonna bitch about it on the forum acussing them of underhanded tactics and link them to Microsoft.

BTW if i remember 9.04 has a policykit dialog from gnome in kubuntu. talk about a pure KDE system.

---

### Post by Oceanwatcher on 2009-07-03
Save your sarkasm for someone that cares!

I am NOT angry because I got some extra files. I have more diskspace. I do not pretend I can keep my system free of all Gnome libs. 

BUT - I do care about being asked and get the chance to refuse if I decide I do not need it. And I do care about someone pretending to install one thing and then pushing a whole package of stuff to someone that did not ask for it.

I actually did not ask to get the UbuntuOne client installed at all. All I wanted in the first place was the PPA. And then I got the whole load without being able to object to it.

And UbuntuOne certainly do not need Synaptic to function. That is just crap from you. I do not need Synaptic. I have apt-get and it works very well. I also have the GUI for it (KpackageKit), not totally there yet, but it does an ok job.

So before you decide to come with some more off-topic nonsense, please try to install the PPA on a Kubuntu system and experience for yourself what this is about.

When someone click "Install PPA" they need to be able to trust that this is what is being installed - two lines of text in the sources and a license. NOT a software package! That belongs under a different button.

---

### Post by steveneddy on 2009-07-03
Why didn't you just install the two lines in sources.list yourself manually?

Did you actually read about what you were going to be doing before you actually pushed the "Install" button?

```
gksudo kate /etc/apt/sources.list
```

---

### Post by juancarlospaco on 2009-07-03
kdesu dolphin /etc/apt/sources.list.d/
[I]
theres no gksudo on KDE, and ubuntuone ppa uses a separated sources.list not the main sources.list[/I]

---

### Post by Oceanwatcher on 2009-07-03
I know very well how to add a PPA to the sources :-)

And yes, I have read what there was to be read. Not much. Did you try UbuntuOne on a Kubuntu installation yourself?

The installation is on this page. It clearly say that the PPA's has to be added first. Then there is a button for installation of the client.

[https://ubuntuone.com/support/installation/](https://ubuntuone.com/support/installation/)

Nowhere on this page is there a link or mention of the addresses and the key for the PPA. If there were, I would probably have used it over the button.

What I expected was two lines in the sources and the key. This is what I got. Do you really need all this to add the PPA's?:

```
Log started: 2009-07-03  19:52:48
Selecting previously deselected package sgml-data.
(Reading database ... 166665 files and directories currently installed.)
Unpacking sgml-data (from .../sgml-data_2.0.3_all.deb) ...              
Selecting previously deselected package docbook-xml.                    
Unpacking docbook-xml (from .../docbook-xml_4.5-6_all.deb) ...          
Selecting previously deselected package libgtop2-common.                
Unpacking libgtop2-common (from .../libgtop2-common_2.26.0-0ubuntu2_all.deb) ...
Selecting previously deselected package libgtop2-7.                             
Unpacking libgtop2-7 (from .../libgtop2-7_2.26.0-0ubuntu2_i386.deb) ...         
Selecting previously deselected package libgksu2-0.                             
Unpacking libgksu2-0 (from .../libgksu2-0_2.0.9-1ubuntu3_i386.deb) ...          
Selecting previously deselected package gksu.                                   
Unpacking gksu (from .../gksu_2.0.2-1ubuntu2_i386.deb) ...                      
Selecting previously deselected package libgtkhtml2-0.                          
Unpacking libgtkhtml2-0 (from .../libgtkhtml2-0_2.11.1-2ubuntu1_i386.deb) ...   
Selecting previously deselected package python-gtkhtml2.                        
Unpacking python-gtkhtml2 (from .../python-gtkhtml2_2.19.1-0ubuntu14_i386.deb) ...
Selecting previously deselected package liblaunchpad-integration1.                
Unpacking liblaunchpad-integration1 (from .../liblaunchpad-integration1_0.1.24_i386.deb) ...
Selecting previously deselected package python-launchpad-integration.                       
Unpacking python-launchpad-integration (from .../python-launchpad-integration_0.1.24_i386.deb) ...
Selecting previously deselected package python-sexy.                                              
Unpacking python-sexy (from .../python-sexy_0.1.9-1ubuntu2_i386.deb) ...                          
Selecting previously deselected package libvte-common.                                            
Unpacking libvte-common (from .../libvte-common_1%3a0.20.0-0ubuntu2_all.deb) ...                  
Selecting previously deselected package libvte9.                                                  
Unpacking libvte9 (from .../libvte9_1%3a0.20.0-0ubuntu2_i386.deb) ...                             
Selecting previously deselected package libscrollkeeper0.                                         
Unpacking libscrollkeeper0 (from .../libscrollkeeper0_0.3.14-16ubuntu1_i386.deb) ...              
Selecting previously deselected package scrollkeeper.                                             
Unpacking scrollkeeper (from .../scrollkeeper_0.3.14-16ubuntu1_i386.deb) ...                      
Selecting previously deselected package synaptic.                                                 
Unpacking synaptic (from .../synaptic_0.62.5ubuntu3_i386.deb) ...                                 
Selecting previously deselected package gnome-app-install.                                        
Unpacking gnome-app-install (from .../gnome-app-install_0.5.24-0ubuntu1.1_all.deb) ...            
Selecting previously deselected package python-vte.                                               
Unpacking python-vte (from .../python-vte_1%3a0.20.0-0ubuntu2_i386.deb) ...                       
Selecting previously deselected package apturl.                                                   
Unpacking apturl (from .../apturl_0.3.3ubuntu1.1_all.deb) ...                                     
Selecting previously deselected package libcairo-perl.                                            
Unpacking libcairo-perl (from .../libcairo-perl_1.060-1_i386.deb) ...                             
Selecting previously deselected package libglib-perl.                                             
Unpacking libglib-perl (from .../libglib-perl_1%3a1.190-2_i386.deb) ...                           
Selecting previously deselected package libgtk2-perl.                                             
Unpacking libgtk2-perl (from .../libgtk2-perl_1%3a1.190-1ubuntu1_i386.deb) ...                    
Selecting previously deselected package libgnome2-canvas-perl.                                    
Unpacking libgnome2-canvas-perl (from .../libgnome2-canvas-perl_1.002-1+b1ubuntu3_i386.deb) ...   
Selecting previously deselected package libgnome2-vfs-perl.                                       
Unpacking libgnome2-vfs-perl (from .../libgnome2-vfs-perl_1.080-1build2_i386.deb) ...             
Selecting previously deselected package libgnome2-perl.                                           
Unpacking libgnome2-perl (from .../libgnome2-perl_1.042-1build2_i386.deb) ...                     
Selecting previously deselected package software-properties-gtk.                                  
Unpacking software-properties-gtk (from .../software-properties-gtk_0.71.5_all.deb) ...           
Processing triggers for man-db ...                                                                
Processing triggers for shared-mime-info ...                                                      
Unknown media type in type 'all/all'                                                              

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up sgml-data (2.0.3) ...

Setting up docbook-xml (4.5-6) ...

Setting up libgtop2-common (2.26.0-0ubuntu2) ...
Setting up libgtop2-7 (2.26.0-0ubuntu2) ...     

Setting up libgksu2-0 (2.0.9-1ubuntu3) ...

Setting up gksu (2.0.2-1ubuntu2) ...

Setting up libgtkhtml2-0 (2.11.1-2ubuntu1) ...

Setting up python-gtkhtml2 (2.19.1-0ubuntu14) ...

Setting up liblaunchpad-integration1 (0.1.24) ...

Setting up python-launchpad-integration (0.1.24) ...

Setting up python-sexy (0.1.9-1ubuntu2) ...
Setting up libvte-common (1:0.20.0-0ubuntu2) ...
Setting up libvte9 (1:0.20.0-0ubuntu2) ...      

Setting up libscrollkeeper0 (0.3.14-16ubuntu1) ...

Setting up scrollkeeper (0.3.14-16ubuntu1) ...
Rebuilding the database. This may take some time.

Setting up synaptic (0.62.5ubuntu3) ...

Setting up gnome-app-install (0.5.24-0ubuntu1.1) ...
Caching application data...
Generating mime/codec maps...

Setting up python-vte (1:0.20.0-0ubuntu2) ...

Setting up apturl (0.3.3ubuntu1.1) ...

Setting up libcairo-perl (1.060-1) ...
Setting up libglib-perl (1:1.190-2) ...
Setting up libgtk2-perl (1:1.190-1ubuntu1) ...
Setting up libgnome2-canvas-perl (1.002-1+b1ubuntu3) ...
Setting up libgnome2-vfs-perl (1.080-1build2) ...
Setting up libgnome2-perl (1.042-1build2) ...
Setting up software-properties-gtk (0.71.5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Log ended: 2009-07-03  19:53:20
```

---

### Post by Vanishing on 2009-07-04
> **Oceanwatcher said:**
> I know very well how to add a PPA to the sources :-)

And yes, I have read what there was to be read. Not much. Did you try UbuntuOne on a Kubuntu installation yourself?

The installation is on this page. It clearly say that the PPA's has to be added first. Then there is a button for installation of the client.

[https://ubuntuone.com/support/installation/](https://ubuntuone.com/support/installation/)

Nowhere on this page is there a link or mention of the addresses and the key for the PPA. If there were, I would probably have used it over the button.

What I expected was two lines in the sources and the key. This is what I got. Do you really need all this to add the PPA's?:

```
Log started: 2009-07-03  19:52:48
Selecting previously deselected package sgml-data.
(Reading database ... 166665 files and directories currently installed.)
Unpacking sgml-data (from .../sgml-data_2.0.3_all.deb) ...              
Selecting previously deselected package docbook-xml.                    
Unpacking docbook-xml (from .../docbook-xml_4.5-6_all.deb) ...          
Selecting previously deselected package libgtop2-common.                
Unpacking libgtop2-common (from .../libgtop2-common_2.26.0-0ubuntu2_all.deb) ...
Selecting previously deselected package libgtop2-7.                             
Unpacking libgtop2-7 (from .../libgtop2-7_2.26.0-0ubuntu2_i386.deb) ...         
Selecting previously deselected package libgksu2-0.                             
Unpacking libgksu2-0 (from .../libgksu2-0_2.0.9-1ubuntu3_i386.deb) ...          
Selecting previously deselected package gksu.                                   
Unpacking gksu (from .../gksu_2.0.2-1ubuntu2_i386.deb) ...                      
Selecting previously deselected package libgtkhtml2-0.                          
Unpacking libgtkhtml2-0 (from .../libgtkhtml2-0_2.11.1-2ubuntu1_i386.deb) ...   
Selecting previously deselected package python-gtkhtml2.                        
Unpacking python-gtkhtml2 (from .../python-gtkhtml2_2.19.1-0ubuntu14_i386.deb) ...
Selecting previously deselected package liblaunchpad-integration1.                
Unpacking liblaunchpad-integration1 (from .../liblaunchpad-integration1_0.1.24_i386.deb) ...
Selecting previously deselected package python-launchpad-integration.                       
Unpacking python-launchpad-integration (from .../python-launchpad-integration_0.1.24_i386.deb) ...
Selecting previously deselected package python-sexy.                                              
Unpacking python-sexy (from .../python-sexy_0.1.9-1ubuntu2_i386.deb) ...                          
Selecting previously deselected package libvte-common.                                            
Unpacking libvte-common (from .../libvte-common_1%3a0.20.0-0ubuntu2_all.deb) ...                  
Selecting previously deselected package libvte9.                                                  
Unpacking libvte9 (from .../libvte9_1%3a0.20.0-0ubuntu2_i386.deb) ...                             
Selecting previously deselected package libscrollkeeper0.                                         
Unpacking libscrollkeeper0 (from .../libscrollkeeper0_0.3.14-16ubuntu1_i386.deb) ...              
Selecting previously deselected package scrollkeeper.                                             
Unpacking scrollkeeper (from .../scrollkeeper_0.3.14-16ubuntu1_i386.deb) ...                      
Selecting previously deselected package synaptic.                                                 
Unpacking synaptic (from .../synaptic_0.62.5ubuntu3_i386.deb) ...                                 
Selecting previously deselected package gnome-app-install.                                        
Unpacking gnome-app-install (from .../gnome-app-install_0.5.24-0ubuntu1.1_all.deb) ...            
Selecting previously deselected package python-vte.                                               
Unpacking python-vte (from .../python-vte_1%3a0.20.0-0ubuntu2_i386.deb) ...                       
Selecting previously deselected package apturl.                                                   
Unpacking apturl (from .../apturl_0.3.3ubuntu1.1_all.deb) ...                                     
Selecting previously deselected package libcairo-perl.                                            
Unpacking libcairo-perl (from .../libcairo-perl_1.060-1_i386.deb) ...                             
Selecting previously deselected package libglib-perl.                                             
Unpacking libglib-perl (from .../libglib-perl_1%3a1.190-2_i386.deb) ...                           
Selecting previously deselected package libgtk2-perl.                                             
Unpacking libgtk2-perl (from .../libgtk2-perl_1%3a1.190-1ubuntu1_i386.deb) ...                    
Selecting previously deselected package libgnome2-canvas-perl.                                    
Unpacking libgnome2-canvas-perl (from .../libgnome2-canvas-perl_1.002-1+b1ubuntu3_i386.deb) ...   
Selecting previously deselected package libgnome2-vfs-perl.                                       
Unpacking libgnome2-vfs-perl (from .../libgnome2-vfs-perl_1.080-1build2_i386.deb) ...             
Selecting previously deselected package libgnome2-perl.                                           
Unpacking libgnome2-perl (from .../libgnome2-perl_1.042-1build2_i386.deb) ...                     
Selecting previously deselected package software-properties-gtk.                                  
Unpacking software-properties-gtk (from .../software-properties-gtk_0.71.5_all.deb) ...           
Processing triggers for man-db ...                                                                
Processing triggers for shared-mime-info ...                                                      
Unknown media type in type 'all/all'                                                              

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up sgml-data (2.0.3) ...

Setting up docbook-xml (4.5-6) ...

Setting up libgtop2-common (2.26.0-0ubuntu2) ...
Setting up libgtop2-7 (2.26.0-0ubuntu2) ...     

Setting up libgksu2-0 (2.0.9-1ubuntu3) ...

Setting up gksu (2.0.2-1ubuntu2) ...

Setting up libgtkhtml2-0 (2.11.1-2ubuntu1) ...

Setting up python-gtkhtml2 (2.19.1-0ubuntu14) ...

Setting up liblaunchpad-integration1 (0.1.24) ...

Setting up python-launchpad-integration (0.1.24) ...

Setting up python-sexy (0.1.9-1ubuntu2) ...
Setting up libvte-common (1:0.20.0-0ubuntu2) ...
Setting up libvte9 (1:0.20.0-0ubuntu2) ...      

Setting up libscrollkeeper0 (0.3.14-16ubuntu1) ...

Setting up scrollkeeper (0.3.14-16ubuntu1) ...
Rebuilding the database. This may take some time.

Setting up synaptic (0.62.5ubuntu3) ...

Setting up gnome-app-install (0.5.24-0ubuntu1.1) ...
Caching application data...
Generating mime/codec maps...

Setting up python-vte (1:0.20.0-0ubuntu2) ...

Setting up apturl (0.3.3ubuntu1.1) ...

Setting up libcairo-perl (1.060-1) ...
Setting up libglib-perl (1:1.190-2) ...
Setting up libgtk2-perl (1:1.190-1ubuntu1) ...
Setting up libgnome2-canvas-perl (1.002-1+b1ubuntu3) ...
Setting up libgnome2-vfs-perl (1.080-1build2) ...
Setting up libgnome2-perl (1.042-1build2) ...
Setting up software-properties-gtk (0.71.5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Log ended: 2009-07-03  19:53:20
```

If you don't trust them, add the ppa manually.


and FYI: if they don't need the libraries, why would they put them in there?

---

### Post by Oceanwatcher on 2009-07-04
> **Vanishing said:**
> If you don't trust them, add the ppa manually.


and FYI: if they don't need the libraries, why would they put them in there?

Yeah, as I said a little further up in the thread:


> [https://ubuntuone.com/support/installation/](https://ubuntuone.com/support/installation/)

Nowhere on this page is there a link or mention of the addresses and the key for the PPA. If there were, I would probably have used it over the button.

I really DID trust them... until yesterday! Don't worry though, I am getting help elsewhere to uninstall it.

---

### Post by howefield on 2009-07-04
I wonder why the dirty rotters called it Ubuntuone, and not Kubuntuone or some such thing. rofl.

---

### Post by Oceanwatcher on 2009-07-04
And I wonder why they call this a friendly forum...

Seriously - they said this would be ok on any UbuntuBASED system.

And it does not really matter what you call it, when you say you will do one thing, don't do something else. It is all about communicating clearly.

Enough now. I'm gone from this thread. If anyone else feel like having fun here, be my guest ):P

---

### Post by howefield on 2009-07-04
> **Oceanwatcher said:**
> Seriously - they said this would be ok on any UbuntuBASED system.

And it does not really matter what you call it, when you say you will do one thing, don't do something else. It is all about communicating clearly.

Seriously, how clear can they be ?

Quote from the install page that you will have read prior to starting an install....

> Installation Instructions

Requirements: Because we want to give everyone using Ubuntu One the very best experience, we require that you run Ubuntu 9.04 (Jaunty Jackalope).

---

