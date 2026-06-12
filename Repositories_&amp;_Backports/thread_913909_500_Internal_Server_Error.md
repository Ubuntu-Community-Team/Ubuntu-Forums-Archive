---
title: "500 Internal Server Error"
date: 2008-09-08
forum: Repositories &amp; Backports
---

### Post by nick937 on 2008-09-08
whats going on with this???


```

nick@t00r:~$ sudo apt-get update
[sudo] password for nick: 
Ign http://repository.akirad.net akirad-hardy Release.gpg
Ign http://people.debian.org woody/ Release.gpg                                
Ign http://people.debian.org woody/ Translation-en_US                          
Ign http://repository.akirad.net akirad-hardy/main Translation-en_US           
Get:1 http://people.debian.org woody/ Release                                  
Hit http://packages.medibuntu.org hardy Release.gpg                            
Hit http://archive.ubuntu.com hardy Release.gpg                                
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Ign http://repository.akirad.net akirad-hardy Release                          
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://people.debian.org woody/ Packages                                   
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://people.debian.org woody/ Packages                                   
Ign http://repository.akirad.net akirad-hardy/main Packages                    
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US               
Ign http://archive.ubuntu.com hardy/universe Translation-en_US                 
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US               
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US             
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US       
Hit http://archive.ubuntu.com hardy-backports Release.gpg                      
Hit http://archive.canonical.com hardy Release                                 
Err http://repository.akirad.net akirad-hardy/main Packages                    
  500 Internal Server Error
Get:2 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_US           
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_US     
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_US       
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_US     
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://archive.ubuntu.com hardy-security Release.gpg             
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-proposed Release.gpg             
Ign http://archive.ubuntu.com hardy-proposed/restricted Translation-en_US
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://archive.canonical.com hardy/partner Sources                         
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://archive.ubuntu.com hardy-proposed/main Translation-en_US            
Ign http://archive.ubuntu.com hardy-proposed/multiverse Translation-en_US      
Ign http://archive.ubuntu.com hardy-proposed/universe Translation-en_US        
Hit http://archive.ubuntu.com hardy Release                                    
Hit http://archive.ubuntu.com hardy-updates Release                            
Hit http://archive.ubuntu.com hardy-backports Release                          
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://archive.ubuntu.com hardy-security Release                           
Hit http://archive.ubuntu.com hardy-proposed Release                
Hit http://packages.medibuntu.org hardy Release                                
Hit http://archive.ubuntu.com hardy/main Packages                              
Hit http://archive.ubuntu.com hardy/restricted Packages             
Hit http://archive.ubuntu.com hardy/main Sources                    
Hit http://archive.ubuntu.com hardy/restricted Sources              
Hit http://archive.ubuntu.com hardy/universe Packages               
Hit http://archive.ubuntu.com hardy/universe Sources                
Hit http://ppa.launchpad.net hardy/main Sources                     
Hit http://archive.ubuntu.com hardy/multiverse Packages            
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy-updates/main Packages                      
Hit http://archive.ubuntu.com hardy-updates/restricted Packages                
Hit http://archive.ubuntu.com hardy-updates/main Sources                       
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://archive.ubuntu.com hardy-updates/restricted Sources                 
Hit http://archive.ubuntu.com hardy-updates/universe Packages                  
Hit http://archive.ubuntu.com hardy-updates/universe Sources                   
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages                
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources                 
Hit http://archive.ubuntu.com hardy-backports/main Packages                    
Hit http://archive.ubuntu.com hardy-backports/restricted Packages              
Hit http://archive.ubuntu.com hardy-backports/universe Packages                
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages              
Hit http://archive.ubuntu.com hardy-security/main Packages                     
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/universe Sources
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Hit http://archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://archive.ubuntu.com hardy-proposed/main Packages
Hit http://archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://archive.ubuntu.com hardy-proposed/universe Packages
Fetched 1B in 1s (1B/s)  
W: Failed to fetch http://repository.akirad.net/dists/akirad-hardy/main/binary-amd64/Packages.gz  500 Internal Server Error

E: Some index files failed to download, they have been ignored, or old ones used instead.
nick@t00r:~$ 

```

---

### Post by forger on 2008-09-08
Looks like you have to use other mirrors(?)
If you go to: [http://repository.akirad.net/dists/akirad-hardy/main/binary-amd64/Packages.gz](http://repository.akirad.net/dists/akirad-hardy/main/binary-amd64/Packages.gz)
You'll see the same error.

I've found two other mirrors you could try and use:
[http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key)
[http://repository.akirad.net/dists/hardy.list](http://repository.akirad.net/dists/hardy.list)

> ## Akirad-Hardy - Ubuntu 8.04 "Hardy Heron"
## Please report any bug on akir4d at gmail.com

## mirror1
deb [http://akirad.cinelerra.org/](http://akirad.cinelerra.org/) akirad-hardy main #Akirad Repository - Mirror1

#deb-src [http://akirad.cinelerra.org/](http://akirad.cinelerra.org/) akirad-hardy main #Akirad Repository - Mirror1


## mirror2
#deb [http://akirad.hfbk.net/](http://akirad.hfbk.net/) akirad-hardy main #Akirad Repository - Mirror2

#deb-src [http://akirad.hfbk.net/](http://akirad.hfbk.net/) akirad-hardy main #Akirad Repository - Mirror2

Note that you could report any problems to that email too

---

### Post by regala on 2008-09-08
> **forger said:**
> Looks like you have to use other mirrors(?)
If you go to: [http://repository.akirad.net/dists/akirad-hardy/main/binary-amd64/Packages.gz](http://repository.akirad.net/dists/akirad-hardy/main/binary-amd64/Packages.gz)
You'll see the same error.

I've found two other mirrors you could try and use:
[http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key)
[http://repository.akirad.net/dists/hardy.list](http://repository.akirad.net/dists/hardy.list)



Note that you could report any problems to that email too


I think I am delusional...
how could you answer to such an impolite, rude way of writing request ??

there are times when you have to tell newbies when they **** up with their behaviour.

---

### Post by Marshal0505 on 2008-09-08
> **regala said:**
> I think I am delusional...
how could you answer to such an impolite, rude way of writing request ??

there are times when you have to tell newbies when they **** up with their behaviour.

Different people means different frame of reference? Goes for behaviour too imo.Besides,we're not all native english speakers.I'm not and these nuances tend to go by me without noticing.

---

### Post by forger on 2008-09-08
Sometimes you just have to overcome some language barriers.. most of the time people don't understand that what they had written was wrong.

Unless their post directly insults me or any other individual, I haven't got a problem helping them out, as well as point them out that their request was wrongly put. Guess I sometimes forget the last part :)

---

### Post by kabel_kabel on 2008-09-10
May i ask what is polite way of asking question?

English is not my native language, and i apologize if we non speaking English people insulted you. If you think that was not polite way of asking question, why don't you moderators post policy of asking questions in this forum and put it at the very beginning of this forum so everybody could see it and follow it.

BTW, i am volunteer at hospital and i enjoy helping people and the rule of thumb (before you start helping) is that if you expect someone to thank you then quit helping.

My apologies one more time,
Kabel

---

### Post by akir4d on 2008-09-20
Install addakirad.deb that fix all my repository errors, follow:

[http://cinelerra.org/getting_cinelerra.php#ubuntu]("http://cinelerra.org/getting_cinelerra.php#ubuntu")

or

[http://akiradproject.net/repository]("http://akiradproject.net/repository")

byez

Paolo Rampino aka Akirad

---

