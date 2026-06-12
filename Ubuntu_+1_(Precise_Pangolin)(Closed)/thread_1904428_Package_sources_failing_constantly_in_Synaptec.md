---
title: "Package sources failing constantly in Synaptec"
date: 2012-01-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Robertjm on 2012-01-04
I've noticed something over the past few days, but don't see any other comments about it so figured I would ask.

I have been using Synaptec for updating over the past several days. When I do, there's a whole bunch of software sources that constantly fail immediately when hitting the Reload buttom. I believer these are sources that came with the install and not something that I necessarily added. Before posting this I ran sudo apt-get update from the command line and these are listed as "ign" on their line. Does that mean "ignore?"

Here are all the sources I got the ign on:

Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                                                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                                                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                                                                           
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en


Are there some sources that should have been removed by an update, but weren't for whatever reason?

Robert

---

### Post by effenberg0x0 on 2012-01-04
> **Robertjm said:**
> I've noticed something over the past few days, but don't see any other comments about it so figured I would ask.

I have been using Synaptec for updating over the past several days. When I do, there's a whole bunch of software sources that constantly fail immediately when hitting the Reload buttom. I believer these are sources that came with the install and not something that I necessarily added. Before posting this I ran sudo apt-get update from the command line and these are listed as "ign" on their line. Does that mean "ignore?"

Here are all the sources I got the ign on:

Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                                                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                                                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                                                                           
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en


Are there some sources that should have been removed by an update, but weren't for whatever reason?

Robert

Please, post your /etc/apt/sources.list and /etc/apt/sources.list.d/*, so we can have a better idea of what's going on there.
```

$ sudo cat /etc/apt/sources.list

``````

$ for file in $(ls /etc/apt/sources.list.d/*); do echo -e "$(basename $file)\n"; sudo cat $file; echo -e "\n\n"; done

```

---

### Post by cariboo on 2012-01-04
That looks pretty normal to me, are you having a problem updating otherwise.

---

### Post by Robertjm on 2012-01-04
Per your request, files are attached. As to the other person's question, nope. Just wondering what's up with these particular repos is all.

Robert

> **effenberg0x0 said:**
> Please, post your /etc/apt/sources.list and /etc/apt/sources.list.d/*, so we can have a better idea of what's going on there.
```

$ sudo cat /etc/apt/sources.list

``````

$ for file in $(ls /etc/apt/sources.list.d/*); do echo -e "$(basename $file)\n"; sudo cat $file; echo -e "\n\n"; done

```

---

