---
title: "How To: openVAS 4.0"
date: 2011-05-10
forum: Security
---

### Post by cprofitt on 2011-05-10
I have worked over the last three days to get openVAS 4.0 working on Ubuntu Server 11.04. I have a feeling that the same process would work for 10.04 and 10.10 if the repository is changed.

Here is what I did to get the server up and running.

Step 1: Configure OBS Repository
[PHP]
sudo apt-get -y install python-software-properties
sudo add-apt-repository "deb http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_11.04/ ./"
[/PHP]Other repositories are:

10.04
> 
"deb [http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_10.04/]("http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_11.04/") ./"
10.10
> 
"deb [http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_10.10/]("http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_11.04/") ./"
You have to remove the 'source' entry in /etc/apt/sources.list


> 
sudo nano /etc/apt/sources.list
Now you can continue adding the repository
> 
sudo apt-key adv --keyserver hkp://keys.gnupg.net --recv-keys BED1E87979EAFD54
sudo apt-get update
Step 2: Quick-Install OpenVAS
> 
sudo apt-get -y install greenbone-security-assistant gsd openvas-cli openvas-manager openvas-scanner openvas-administrator sqlite3 xsltproc
Step 3: Quick-Start OpenVAS
> 
test -e /var/lib/openvas/CA/cacert.pem  || sudo openvas-mkcert -q
sudo openvas-nvt-sync
test -e /var/lib/openvas/users/om || sudo openvas-mkcert-client -n om -i
sudo /etc/init.d/openvas-manager stop
sudo /etc/init.d/openvas-scanner stop
sudo touch sudo touch /var/lib/openvas/mgr/tasks.db
sudo chmod 600 /var/lib/openvas/mgr/tasks.db
sudo openvassd
sudo openvasmd --migrate
sudo openvasmd --rebuild
sudo killall openvassd
sleep 15
sudo /etc/init.d/openvas-scanner start
sudo /etc/init.d/openvas-manager start
sudo /etc/init.d/openvas-administrator restart
test -e /var/lib/openvas/users/admin || sudo openvasad -c add_user -n admin -r Admin
sudo gsad
Add the components to startup by adding them to the rc.local file
> 
sudo nano /etc/rc.local
add the following:
> 
 openvassd
 openvasad
 openvasmd
 gsad
The next post will explore making use of the base system.

[Part 2]("http://ubuntuforums.org/showpost.php?p=10827628&postcount=8")
[Part 3]("http://ubuntuforums.org/showpost.php?p=10827698&postcount=9")
[Part 4]("http://ubuntuforums.org/showpost.php?p=10827738&postcount=10")

---

### Post by josephmills on 2011-05-10
hi there dont know if this will help I am also struggling with it on ubuntu 10.10 but have got it to work fine with this [http://www.blackbuntu.com](http://www.blackbuntu.com) after trying this on ubutnu 10.10 it fails I cant get a key 
```
bobweaver@bobweaver-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-key adv --keyserver hkp://keys.gnupg.net --recv-keys BED1E87979EAFD54
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keys.gnupg.net --recv-keys BED1E87979EAFD54
gpg: requesting key 79EAFD54 from hkp server keys.gnupg.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
bobweaver@bobweaver-Compaq-Presario-CQ60-Notebook-PC
```

---

### Post by cprofitt on 2011-05-10
Odd about the key -- not sure why that is happening.

I have it working now consistently with what I posted on 11.04.

---

### Post by josephmills on 2011-05-10
it was my firewall the settings where to high would not let any other thing in. works great thanks

---

### Post by Nicke on 2011-05-12
Great howto! Thanks!

> **cprofitt said:**
> 
The next post will explore making use of the base system.

I can't wait!

---

### Post by crypiejay on 2011-05-12
I followed the above instructions to the T and I am still getting a protocol error when connecting the openvas-client to the server. I have no idea what is wrong at this point. I have tried everything from the default install and setting up with the ubuntu repos to compiling it myself and I'm still getting the same error.

---

### Post by Nicke on 2011-05-13
> **crypiejay said:**
> I followed the above instructions to the T and I am still getting a protocol error when connecting the openvas-client to the server. I have no idea what is wrong at this point. I have tried everything from the default install and setting up with the ubuntu repos to compiling it myself and I'm still getting the same error.

Try to change the openvas-client portnumber to: 9391 on the login screen, it helped me.

---

### Post by cprofitt on 2011-05-17
--- part 2 ---

Open a web browser and go to your server

You will be prompted for a login

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192428&stc=1&d=1305646699[/IMG]
Login with the admin user you created in the setup.

After login you will be greeted with a screen that looks like this.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192429&stc=1&d=1305647044[/IMG]

The first step to get your system scanning is to define your targets. You can not setup any tasks until those are setup. Click 'Targets'.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192430&stc=1&d=1305647063[/IMG]

Now you can fill out as many targets as you like. Targets can be dns names, a single IP address or a range of IP addresses.

> 
**New Target**

         For creating a new target the dialog offers these entries.        Hit the button "Create Target" to submit the new target.        The list of targets will be updated.       
         Note on **Hosts**:         

[LIST]
[*]             The hosts parameter is a comma-separated list of values.  Each value             can be
[LIST]
[*]an IPv4 address (e.g. 192.168.13.1)
[*]a hostname (e.g. myhost1.domain)
[*]an IPv4 address range in long format                   (e.g. 192.168.1.116-192.168.1.124)
[*]an IPv4 address range in short format                   (e.g. 192.168.1.116-124)
[*]an IPv4 address range in CIDR notation                   (e.g. 192.168.13.0/24)
[*]an IPv6 address                   (e.g. fe80::222:64ff:fe76:4cea/64).
[/LIST]
             These options can be mixed (e.g.             192.168.13.1, myhost2.domain, 192.168.13.0/24).
[*]             The netmask in CIDR notation is limited to 20 (4095 hosts).
[*]             The Scanner currently expects IPv6 addresses to name a single host,             and always replaces the netmasks of IPv6 addresses with 128.
[/LIST]
Once you have created your targets your screen should look like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192431&stc=1&d=1305647466[/IMG]

Now you need to setup new tasks that make use of your 'targets'.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192432&stc=1&d=1305647701[/IMG]

---

### Post by cprofitt on 2011-05-17
Once you have entered your targets and chosen the scan type you are unable to modify the scan type. To choose a new scan type for a target you would have to create a new task. (we will cover schedules later as well).

Once you have created your target list you can click on targets to get to your list.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192434&stc=1&d=1305647962[/IMG]

From here you can run the task, restart the task, stop the task, delete the task, view reports associated with the task and edit the task. As stated previously you can not change the scan type for the target when editing.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192436&stc=1&d=1305648125[/IMG]

Be warned that running large IP address ranges can take a significant amount of time. the /24 scan I did took 5 hours and 37 minutes to complete. The task will refresh on a schedule if you choose that option.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192448&stc=1&d=1305649748[/IMG]
When the run is complete you will be able to view a summary or detailed report. Also, note the run button turned in to a pause button.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192447&stc=1&d=1305649575[/IMG]

The summary view will show you the overall security risk level that machine has (High above). You can then drill down and get more detail by clicking on the blue magnifying glass.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192446&stc=1&d=1305649575[/IMG]

This view shows you the summary of how many 'vulnerabilities' the scanner found at each level. To get even more detail you again click the magnifying glass. 

(continued)

---

### Post by cprofitt on 2011-05-17
--- part 4 ---
The next level of detail shows high and medium items and presents options to download reports. The PDF generation has not worked for me, but HTML has.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192443&stc=1&d=1305649329[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192444&stc=1&d=1305649329[/IMG]

For me this tool has worked to make me more aware of potential issues. You have to be careful to read the 'vulnerabilities' because I have found some of them to not be applicable because the server is not actually running the service selected.

---

### Post by cprofitt on 2011-05-23
I have broken my scans down to match 2-4 servers each and the scan times are running about 3 minutes a target on Full Fast Ultimate setting.

---

### Post by sdmike6 on 2011-07-05
The OpenSuse repository given is a dead link:

```
W: Failed to fetch http://download.opensuse.org/reposit...xUbuntu_11.04/./Sources  404  Not Found

W: Failed to fetch http://download.opensuse.org/reposit...xUbuntu_11.04/./Packages  404  Not Found
```

Is there repository I can use that will work with Ubuntu x64 11.04?

---

### Post by cprofitt on 2011-07-05
> **sdmike6 said:**
> The OpenSuse repository given is a dead link:

```
W: Failed to fetch http://download.opensuse.org/reposit...xUbuntu_11.04/./Sources  404  Not Found

W: Failed to fetch http://download.opensuse.org/reposit...xUbuntu_11.04/./Packages  404  Not Found
```Is there repository I can use that will work with Ubuntu x64 11.04?

The repository is working, but the URL is being altered on the forum. Right click on the link and copy the URL or click it and open the web page. Not sure why that URL is being altered and the others are not.

[PHP]
http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_11.04/[/PHP][]("http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_11.04/")

---

### Post by sdmike6 on 2011-07-05
I hit another wall when starting the manager I get an Error that says Error.


using this command:

```
sudo /etc/init.d/openvas-manager start
Starting OpenVAS Manager: ERROR.

```

I checked the openvas log files and I'm nothing seeing anything useful that helps me out why this is happening.....

---

### Post by sdmike6 on 2011-07-05
I ran the openvas check setup script and I got this:


```
openvas-check-setup 2.1.0
  Test completeness and readiness of OpenVAS-4

  Please report us any non-detected problems and
  help us to improve this check routine:
  http://lists.wald.intevation.org/mailman/listinfo/openvas-discuss

  Send us the log-file (/tmp/openvas-check-setup.log) to help analyze the problem.

  Use the parameter --server to skip checks for client tools
  like GSD and OpenVAS-CLI.

Step 1: Checking OpenVAS Scanner ... 
        OK: OpenVAS Scanner is present in version 3.2.4.
        OK: OpenVAS Scanner CA Certificate is present as /var/lib/openvas/CA/cacert.pem.
        OK: NVT collection in /var/lib/openvas/plugins contains 21846 NVTs.
Step 2: Checking OpenVAS Manager ... 
        OK: OpenVAS Manager is present in version 2.0.4.
        OK: OpenVAS Manager client certificate is present as /var/lib/openvas/CA/clientcert.pem.
        OK: OpenVAS Manager database found in /var/lib/openvas/mgr/tasks.db.
        OK: Access rights for the OpenVAS Manager database are correct.
        OK: sqlite3 found, extended checks of the OpenVAS Manager installation enabled.
        OK: OpenVAS Manager database is at revision 41.
        OK: OpenVAS Manager expects database at revision 41.
        OK: Database schema is up to date.
        ERROR: The number of NVTs in the OpenVAS Manager database is too low.
        FIX: Make sure OpenVAS Scanner is running with an up-to-date NVT collection and run 'openvasmd --rebuild'.

 ERROR: Your OpenVAS-4 installation is not yet complete!

Please follow the instructions marked with FIX above and run this
script again.

If you think this result is wrong, please report your observation
and help us to improve this check routine:
http://lists.wald.intevation.org/mailman/listinfo/openvas-discuss
```
Please attach the log-file (/tmp/openvas-check-setup.log) to help us analyze the problem.

---

### Post by sdmike6 on 2011-07-05
I ended up deleting and then rebuilding the database and it worked finally. 

Third time was a charm :)

---

### Post by cprofitt on 2011-07-05
> **sdmike6 said:**
> I ended up deleting and then rebuilding the database and it worked finally. 

Third time was a charm :smile:

Glad to see it worked.

---

### Post by camurgo on 2011-12-07
For anyone interested, it worked perfectly on Ubuntu 11.10, just replace 11.04 with 11.10 on the repository link.

---

### Post by shayno90 on 2011-12-16
sudo apt-key adv --keyserver hkp://keys.gnupg.net --recv-keys
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keys.gnupg.net --recv-keys
root@IRL-DUB-P-LAP-08:/home/sduignan# sudo apt-key adv --keyserver hkp://keys.gnupg.net --recv-keys BED1E87979EAFD54
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keys.gnupg.net --recv-keys BED1E87979EAFD54
gpg: requesting key 79EAFD54 from hkp server keys.gnupg.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Cannot import the key.

Is the issue with the repositories/key/keyserver?

---

### Post by shayno90 on 2011-12-16
Worked using:

wget [http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_10.10/Release.key](http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_10.10/Release.key)
--2011-12-16 14:26:00--  [http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_10.10/Release.key](http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_10.10/Release.key)
Connecting to 192.168.xx.xx:xx... connected.
Proxy request sent, awaiting response... 200 OK
Length: 995 [application/pgp-keys]
Saving to: `Release.key.1'

100%[=========================================================================================>] 995         --.-K/s   in 0.001s  

2011-12-16 14:26:00 (1.86 MB/s) - `Release.key.1' saved [995/995]

Then:

gpg --import Release.key
gpg: directory `/root/.gnupg' created
gpg: new configuration file `/root/.gnupg/gpg.conf' created
gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/root/.gnupg/secring.gpg' created
gpg: keyring `/root/.gnupg/pubring.gpg' created
gpg: /root/.gnupg/trustdb.gpg: trustdb created
gpg: key 79EAFD54: public key "security OBS Project <security@build.opensuse.org>" imported
gpg: Total number processed: 1
gpg:               imported: 1
gpg: no ultimately trusted keys found

Then still not correct:
sudo apt-get update

W: GPG error: [http://download.opensuse.org](http://download.opensuse.org) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BED1E87979EAFD54



Next issue is installing greenbone!

sudo apt-get -y install greenbone-security-assistant gsd openvas-cli openvas-manager openvas-scanner openvas-administrator sqlite3 xsltproc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openvas-scanner is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package greenbone-security-assistant
E: Unable to locate package gsd
E: Unable to locate package openvas-cli
E: Unable to locate package openvas-manager
E: Package 'openvas-scanner' has no installation candidate
E: Unable to locate package openvas-administrator

---

### Post by shayno90 on 2011-12-19
There was problem with the apt-key of GPG release key not being added to the authentication list for trusted apt sources.

[http://www.youtube.com/watch?v=UUZOQsNo_ws&feature=player_embedded#](http://www.youtube.com/watch?v=UUZOQsNo_ws&feature=player_embedded#)!

Apply the same technique to import the Release.key from 
[http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_10.10/](http://download.opensuse.org/repositories/security:/OpenVAS:/STABLE:/v4/xUbuntu_10.10/)

save the key in a gedit file in a .key extension.

Then import the key into apt GUI and finally update your system to begin installing
OpenVAS.

---

### Post by sdmike6 on 2012-01-25
I installed OpenVas on another server and when I connect to the gui I get this error in the terminal

Error: received handshake message out of context

at the same time when I go to [https://localhost:9392/](https://localhost:9392/) gsad takes up %100 of the cpu.

On this [link]("http://seclists.org/openvas/2011/q4/353") I saw a guy with the same issue so I downloaded and installed libmicrohttpd but I'm still getting the same error.

What am I missing here?

I found a resolution [HERE]("http://seclists.org/openvas/2011/q4/354")

---

### Post by SuperFabius on 2012-02-26
Hi all,
to avoid the gsa issue ([https://localhost:9392/](https://localhost:9392/) simply doesn't work), I start gsa in this way on Ubuntu 11.04:

sudo gsad --http-only --listen=127.0.0.1 -p 9392

Then type to your browser to connect:

[http://127.0.0.1:9392/](http://127.0.0.1:9392/)

See [*here*]("http://www.ehacking.net/2011/06/backtrack-5-openvas-tutorial.html") for more infos.

PS: Strange thing I don't understand until now: the "sudo gsad --http-only --listen=127.0.0.1 -p 9392" command seems to work only if typed from terminal, not inside a batch file.....

Cheers ):P

---

