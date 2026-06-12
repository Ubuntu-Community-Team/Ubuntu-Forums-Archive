---
title: "apt-get error messages"
date: 2011-09-15
forum: Server Platforms
---

### Post by badger58 on 2011-09-15
This is for Ubuntu 10.04.  I have set up an apt-mirror and then edited my sources.list to point to the server.  It all seems to work, but I get a bizarre error when running apt-get update.  The output shows a "Ign" for a given section, then several lines later shows an "Err", then a 404 for the identical section.  

As I understand it, Ign means Ignore, meaning that it looked at that section and found nothing to do.  So if it did that, how can it throw a 404 Err almost immediately after?

Sources.list
> 
deb [http://10.254.254.9/ubuntu/](http://10.254.254.9/ubuntu/) lucid main restricted
deb [http://10.254.254.9/ubuntu/](http://10.254.254.9/ubuntu/) lucid-updates main restricted
deb [http://10.254.254.9/ubuntu/](http://10.254.254.9/ubuntu/) lucid universe
deb [http://10.254.254.9/ubuntu/](http://10.254.254.9/ubuntu/) lucid-updates universe
deb [http://10.254.254.9/ubuntu/](http://10.254.254.9/ubuntu/) lucid multiverse
deb [http://10.254.254.9/ubuntu/](http://10.254.254.9/ubuntu/) lucid-updates multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://10.254.254.9/ubuntu](http://10.254.254.9/ubuntu) lucid-security main restricted
deb [http://10.254.254.9/ubuntu](http://10.254.254.9/ubuntu) lucid-security universe
deb [http://10.254.254.9/ubuntu](http://10.254.254.9/ubuntu) lucid-security multiverse
mirror.list on server
> 
set nthreads     20
set _tilde 0
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted  universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted  universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main/debian-installer restricted/debian-installer
deb-amd64-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main/debian-installer restricted/debian-installer
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main/debian-installer
deb-amd64-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main/debian-installer
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main/debian-installer
deb-amd64-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main/debian-installer
deb [http://archive.cloudera.com/debian](http://archive.cloudera.com/debian) lucid-cdh3 contrib
deb [http://www.apache.org/dist/cassandra/debian](http://www.apache.org/dist/cassandra/debian) 08x main
clean [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
Snippet of apt-get update output.
> 
**Ign [http://10.254.254.9](http://10.254.254.9) lucid/main Packages  **                                  
Ign [http://10.254.254.9](http://10.254.254.9) lucid-updates/main Packages                            
Ign [http://10.254.254.9](http://10.254.254.9) lucid-updates/restricted Packages                      
Ign [http://10.254.254.9](http://10.254.254.9) lucid-updates/universe Packages                        
Ign [http://10.254.254.9](http://10.254.254.9) lucid-updates/multiverse Packages                      
Ign [http://10.254.254.9](http://10.254.254.9) lucid-security/main Packages                           
Ign [http://10.254.254.9](http://10.254.254.9) lucid-security/restricted Packages                     
Ign [http://10.254.254.9](http://10.254.254.9) lucid-security/universe Packages                       
Ign [http://10.254.254.9](http://10.254.254.9) lucid-security/multiverse Packages                     
Ign [http://10.254.254.9](http://10.254.254.9) lucid/restricted Packages                              
[B]Ign [http://10.254.254.9](http://10.254.254.9) lucid/universe Packages                                
Ign [http://10.254.254.9](http://10.254.254.9) lucid/multiverse Packages                              
Err [http://10.254.254.9](http://10.254.254.9) lucid/main Packages                                    
  404  Not Found[/B]
Ign [http://10.254.254.9](http://10.254.254.9) lucid-updates/main Packages                            
Ign [http://10.254.254.9](http://10.254.254.9) lucid-updates/restricted Packages                      
Ign [http://10.254.254.9](http://10.254.254.9) lucid-updates/universe Packages                        
Ign [http://10.254.254.9](http://10.254.254.9) lucid-updates/multiverse Packages                      
Ign [http://10.254.254.9](http://10.254.254.9) lucid-security/main Packages                           
Ign [http://10.254.254.9](http://10.254.254.9) lucid-security/restricted Packages                     
Ign [http://10.254.254.9](http://10.254.254.9) lucid-security/universe Packages                       
Ign [http://10.254.254.9](http://10.254.254.9) lucid-security/multiverse Packages                     
Err [http://10.254.254.9](http://10.254.254.9) lucid/restricted Packages                              
  404  Not Found
[B]Err [http://10.254.254.9](http://10.254.254.9) lucid/universe Packages                                
  404  Not Found
Err [http://10.254.254.9](http://10.254.254.9) lucid/multiverse Packages                              
  404  Not Found[/B]
Err [http://10.254.254.9](http://10.254.254.9) lucid-updates/main Packages                            
  404  Not Found


---

### Post by zackwasa on 2011-09-15
most likely there's something wrong with the apt-mirror you set up or it's missing files.

---

### Post by badger58 on 2011-09-16
Does anyone know where the detailed docs are for apt-get?  I've searched endlessly and not seen any decent documentation on the messages.  I don't know what could be missing, I've dumbed down my sources.list to just "deb [http://10.254.254.9/ubuntu/](http://10.254.254.9/ubuntu/) lucid main" and still get conflicting messages of "Ign" and "Err" on platforms that I'm not even using, like i386 (which is not on the mirror).  I just would like at least a clear understanding of what Ign, Err and Hit really mean, and why it keeps looking for files I didn't tell it to.

---

