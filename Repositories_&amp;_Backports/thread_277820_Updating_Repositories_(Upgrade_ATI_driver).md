---
title: "Updating Repositories (Upgrade ATI driver)"
date: 2006-10-15
forum: Repositories &amp; Backports
---

### Post by ThePenguin on 2006-10-15
Hi people, 

I am attempting to upgrade my ATI driver using the [tutorail]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually").

My problem is that I am behind a firewall and am unable to upgrade the repository. Here is the error messages I receive:

> 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.



How do I go about resolving this?

Thanks, 
Hank

---

### Post by catlett on 2006-10-15
You only need 2 packages from the repositories, build-essential and module-assistant. You can download the deb files for those 2 packages here [http://packages.ubuntu.com/](http://packages.ubuntu.com/) Just search for them and download the deb. Gdebi package installer will install them for you. You can either run gdebi when you download or double click the files after they are downloaded to launch gdebi.
If your firewall is because of a proxy, you can get around it by using an anonymous proxy to browse to the dapper package site. Ninja Proxy is one [http://www.ninjaproxy.com/](http://www.ninjaproxy.com/) Just enter the dapper packages url in the search box at the bottom and hit "go". Hopefully the proxy is your issue and now you can download build-essential and module-assistant. After they are installed folow the how to, those 2 packages are the only things you need from the repository. Other than that, I do not know how to get you around your firewall. If you still have issues, post more info about your firewall.

---

### Post by ThePenguin on 2006-10-16
Hi catlett, 

Thanks for the response. 

I downloaded the 2 packages as you said. I only managed to install the "module-assistant_0.10.2_all.deb" file. The "build-essential_11.1_i386.deb" displayes the following error message in the package installer: "Error: Dependency is not satisfiable: libc6-dev | libc-dev", thus the "Install Package" button is disabled. I searched for the files in the package directory but couldn't find a .deb file as with the others. What do I need to do, to install these files? Couldn't I install these files from the ubuntu cd?

---

### Post by catlett on 2006-10-16
build-essential should be on the ubuntu cd. Put the ubuntu cd in and try using Synaptic Package Manager to install build-essential (Synaptic is in the top panel under System<Administration<Synaptic Package Manager)
Synaptic is the same thing as apt-get, it just does it with a GUI instead of command line. It should automatically know the cd is there but if it has an issue, go to Settings, Repositories from inside Synaptic and make sure the CD is checked off on the list of repositories.

---

