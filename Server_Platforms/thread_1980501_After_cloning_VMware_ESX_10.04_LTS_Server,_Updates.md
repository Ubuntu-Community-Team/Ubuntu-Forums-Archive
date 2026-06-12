---
title: "After cloning VMware ESX 10.04 LTS Server, Updates Appear as &quot;NOT AUTHENTICATED&quot;"
date: 2012-05-15
forum: Server Platforms
---

### Post by mtalebi on 2012-05-15
Hello all. We have an Ubuntu 10.04 LTS Server install that we have installed in a VMware ESX virtual machine. We cloned the server to create a new test environment. Everything seems to work on the cloned test machine except all of the Ubuntu software updates appear as NOT AUTHENTICATED. Does anyone have any tips on what I can do to fix this? I've seen various posts online about it but their fixes did not work for us. Our production system does not have problems with updates. I have attached a screen shot. Thank you!

---

### Post by mtalebi on 2012-05-15
I also notice that I cannot ssh to the new test server unless I am logged in locally first. If I logout locally then the ssh connections get terminated and I cannot create a new ssh connection. Could this be related to the problems with the updates?

---

### Post by LHammonds on 2012-05-15
Did you have VMWare Tools installed on the OS before cloning?

EDIT: See the "VMWare Tools" section at the bottom of [this post]("http://ubuntuforums.org/showpost.php?p=11931535&postcount=3") to see what I'm talking about in regards to installing the tools.

---

### Post by mtalebi on 2012-05-15
Good question. I don't think we had VMware tools installed. I will try to do that now but does not having VMware tools installed corrupt a clone?

---

### Post by LHammonds on 2012-05-15
> **mtalebi said:**
> Good question. I don't think we had VMware tools installed. I will try to do that now but does not having VMware tools installed corrupt a clone?
I don't know.  Installing the tools is one of the 1st things I do after bringing a server online.  All I know for sure is that disk performance is not as good without it installed.

---

### Post by mtalebi on 2012-05-16
VMware Tools were installed on the test system and it did not have an effect on my issues.

---

### Post by mtalebi on 2012-05-16
Here is what I get when trying command line update. apt-get can't access these servers but if I use Firefox on the same server I can. 

user@host:/etc/ssh$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
  Connection failed [IP: 91.189.88.28 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                          
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                                                                   
  Connection failed [IP: 91.189.92.181 80]
Err [http://ppa.launchpad.net/groovy-dev/grails/ubuntu/](http://ppa.launchpad.net/groovy-dev/grails/ubuntu/) lucid/main Translation-en_US                                         
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                            
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                                       
  Connection failed [IP: 91.189.92.151 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US                                
  Connection failed [IP: 91.189.92.151 80]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                                            
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US                                          
  Connection failed [IP: 91.189.92.167 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                                            
  Connection failed
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US                                            
  Connection failed [IP: 91.189.92.184 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US                                 
  Connection failed [IP: 91.189.92.153 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
  Connection failed [IP: 91.189.92.155 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages                                           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                                                   
  Connection failed [IP: 91.189.92.176 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                                                   
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US                                
  Connection failed [IP: 91.189.92.179 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources                                             
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US                          
  Connection failed [IP: 91.189.92.181 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US                            
  Connection failed [IP: 91.189.92.183 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                                                  
  Connection failed [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                                                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages                                            
  Connection failed [IP: 91.189.92.184 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages                                           
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                                                   
  Connection failed [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources                                             
  Connection failed [IP: 91.189.92.181 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                                              
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                                              
  Connection failed [IP: 91.189.92.151 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                                                         
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                                               
  Connection failed [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages     
  Connection failed [IP: 91.189.92.192 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
  Connection failed [IP: 91.189.88.22 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources      
  Connection failed [IP: 91.189.88.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
  Connection failed [IP: 91.189.88.26 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
  Connection failed [IP: 91.189.88.29 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources  
  Connection failed [IP: 91.189.92.152 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
  Connection failed [IP: 91.189.92.154 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
  Connection failed [IP: 91.189.92.156 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
  Connection failed [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
  Connection failed [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
  Connection failed [IP: 91.189.92.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
  Connection failed [IP: 91.189.92.184 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Connection failed [IP: 91.189.88.28 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.151 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.153 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.155 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Connection failed [IP: 91.189.92.176 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.179 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.181 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.183 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Connection failed [IP: 91.189.92.181 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.151 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.184 80]

W: Failed to fetch [http://ppa.launchpad.net/groovy-dev/grails/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/groovy-dev/grails/ubuntu/dists/lucid/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/groovy-dev/grails/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/groovy-dev/grails/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/groovy-dev/grails/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/groovy-dev/grails/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  Connection failed [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Connection failed [IP: 91.189.92.181 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.151 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.192 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.88.22 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Connection failed [IP: 91.189.88.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Connection failed [IP: 91.189.88.26 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.88.29 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Connection failed [IP: 91.189.92.152 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.154 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.156 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Connection failed [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Connection failed [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.182 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Connection failed [IP: 91.189.92.184 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by LHammonds on 2012-05-17
I don't know what the problem is.  For Windows servers, we turn base installs into Templates.  We then deploy templates from those images.

For Linux servers, I have always installed from ISO image because I typically fine-tune how the partitions are defined.  Example: [MediaWiki server]("http://ubuntuforums.org/showthread.php?t=1979266")

Try converting the server you want to clone to a template 1st.  Then deploy virtual machine from template.

**EDIT:** You might want to read [this article]("http://pubs.vmware.com/vsphere-4-esx-vcenter/index.jsp?topic=/com.vmware.vsphere.vmadmin.doc_41/vsp_vm_guide/deploy_vms_from_templates_and_clones/t_customize_linux_during_cloning_or_deployment.html") too if you have not already.

LHammonds

---

### Post by mtalebi on 2012-06-04
Ok we found out that our firewall was blocking "apt-get". This is why we could visit the Ubuntu repos using Firefox but apt-get would fail to download the files.

Thanks.

---

### Post by LHammonds on 2012-06-04
Ouch.  Bit by the firewall.  I'm glad you figured out what the problem was and thanks for sharing the solution.

---

