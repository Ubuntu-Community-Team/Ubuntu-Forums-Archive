---
title: "Creating a Trusted Local Repository from which Software Updates can be installed."
date: 2009-03-08
forum: Tutorials
---

### Post by luvr on 2009-03-08
[SIZE="4"][COLOR="DarkRed"]**_Abstract._**[/COLOR][/SIZE]

If you manage multiple PCs running Ubuntu, you will likely want to keep them all updated. Thus, you will want to install the Ubuntu updates to each of them as they become available, and you will have each PC individually download all of the updates from the Ubuntu repositories on the internet. This may, however, be impractical to you—particularly if, e.g., you are on a rather slow internet connection, or if your monthly data transfer volume is severely limited, or if you simply prefer to save the bandwidth.

If you would like to download the updates just once, and further distribute the downloaded files locally, you can set up a **Local Repository.** Basically, a *"repository"* is a directory that contains a set of software packages (i.e., *".deb"* files, in the case of Debian-based distributions—such as Ubuntu), plus an *index* file that lists the packages that are available in the directory. Such a repository, however, is considered *"untrusted"*: the software installer (i.e., the ***"APT"*** system—which includes the *"apt-get"* command, the *"Synaptic Package Manager,"* the *"Update Manager,"* etc.) will ignore any package that is present in the repository whenever another copy of the package is available in another, ***trusted,*** repository—i.e., most likely, on the internet. To create a **trusted** repository, you need to take a few extra steps, in addition to creating the *index* file:
[LIST]
[*]Create a *"release"* file, which is a small text file that contains, among other details, a *checksum* for the index file;
[*]Generate a *digital signature* for the release file, to prevent tampering by unauthorised individuals.
[/LIST]
Whenever the software installer attempts to use the trusted repository, it will verify if the *digital signature* for the *release* file is correct—i.e., if it corresponds to the current contents of the file. If the digital signature is correct, then the installer will trust the contents of the release file—which includes the checksum for the *index* file. If, subsequently, that checksum corresponds to the current contents of the index file, then the contents of that file can be trusted as well. Finally, the index file includes a checksum for each of the packages made available by the repository, so the packages themselves can be verified too.

Thus, before you can set up a **trusted** local repository, you will have to make sure that you can generate a *digital signature* for its release file. To that end, you will have to create a *"GPG Key Pair"* for yourself, and register it (or, more precisely, its *public* key part) as a trusted key for APT to use—so that APT can verify any digital signatures that are generated with this key pair (or, more precisely, with its *private* key part).

[SIZE="4"][COLOR="DarkRed"]**_Step 1: Generating your GPG Key Pair._**[/COLOR][/SIZE]

To generate a GPG key pair, start the following command:
```
gpg --gen-key
```
After some introductory text, the program will ask you which type of key you want to create:
```
Please select what kind of key you want:
   (1) DSA and Elgamal (default)
   (2) DSA (sign only)
   (5) RSA (sign only)
```
Since you will be using your key only for generating *digital signatures,* you don't need option 1, *"DSA and Elgamal,"* (although it will work fine), but you can get by with a *"sign only"* key—i.e., option 2, *"DSA,"* or option 5, *"RSA."* Of these two, RSA is the more powerful, so I suggest you select that:
```
Your selection? **5**
```
If you opt for an RSA key, the program will next ask you what *size* you want for the key; for maximum security, you will most likely want the longest possible key—i.e., 4096 bits (however, longer keys will require more computing resources, so you may prefer a shorter key if your computer is not all too powerful):
```
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048****) **4096**
```
Next, the program will ask you if you want to attach an *expiration date* to the key; if you don't, then the key will remain valid indefinitely:
```
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
```
For a high-risk key (e.g., a key that you will use to digitally prove your identity), it may be critical to set an appropriate expiration date, but the type of key that you are currently generating doesn't really need an expiration date. The default option—i.e., a key that won't expire—is, therefore, perfectly acceptable. Alternatively, you may prefer the key to expire in, say, 5 years or so:
```
Key is valid for? (0) **5y**
```
The program will show you the expiration date and time for the key, and ask you to confirm if that is what you want:
```
Key expires at Thu 06 Mar 2014 21:12:03 CET
Is this correct? (y/N) **Y**
```
Now it's time to specify the *"user id"* for your new key:
```
You need a user ID to identify your key; the software constructs the user ID
from the Real Name, Comment and E-mail Address in this form:
    "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"
```
The program will ask you for the following three items:
[LIST]
[*]**Real name**
For a key that you will use to prove your identity, you should specify your own real name here.
In this case, however, you should really *avoid* using your own name. Technically, you can give the key any name that you like—even something totally unrelated to the function of the key, like *"Bart Bogus"* or *"Teri Hatcher is the Greatest!"* or even *"Who the Hell is Teri Hatcher, anyway?"* will do.
Since you will be using the key to sign your local Ubuntu repository, you should probably name it *"Local Ubuntu Repository"* or (if you want to mention the specific Ubuntu release for which you will be using the key) *"Local Ubuntu Intrepid Ibex Repository"* or some such.
[*]**E-mail address**
You needn't specify an e-mail address for this key.
[*]**Comment**
You needn't specify a comment either.
[/LIST]
So, for example:
```
Real name: **Local Ubuntu Intrepid Ibex Repository**
E-mail address:
Comment:
You selected this USER-ID:
    "Local Ubuntu Intrepid Ibex Repository"
```
You will get a chance to modify the *user id*; if you're satisfied with what you entered, then select **O**kay to continue:
```
Change (N)ame, (C)omment, (E)-mail or (O)kay/(Q)uit? **O**
```
At this point, the program has all the data that it needs to generate your new key. The key will actually consist of two parts:
[LIST]
[*]A *private* (or *secret*) key—which (as the name suggests) you should keep secret, to prevent *"digital identity theft."*
In this case, you don't really reveal your identity, but anyone who gains access to your secret key will be able to create falsely *"trusted"* software repositories that could be installed on any computer that knows about your key.
[*]A *public* key—which you are supposed to distribute to anyone who should be able to verify your identity.
In this particular case, you will add this *public* key to the list of trusted keys on any computer on which you want to install the packages from your local repository.
[/LIST]
It should be obvious that the *secret* key should really be kept secret. Therefore, the program will ask you for a *"passphrase"* (or *"password"*), which will protect your *secret* key:
```
You need a Passphrase to protect your secret key.

Enter passphrase:
```
Select a sufficiently complex passphrase, but one that you can remember—if you ever forget it, then you will lose access to your *secret* key, and you will no longer be able to generate any digital signatures with it.

You will have to repeat your passphrase:
```
Repeat passphrase:
```
Finally, the program will begin to compute your new key pair:
```
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, use the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
```
You should really follow the advice that the program gives you, and keep your system busy. If you don't, then the program will complain that it cannot generate enough random bytes for your key—and it will make you wait until it can:
```
...+++++

Not enough random bytes available.  Please do some other work to give
the OS a chance to collect more entropy!  (Need 182 more bytes)
.....................................+++++
```
Once your new key pair is ready, the program will produce the following output:
```
gpg: /home/luvr/.gnupg/trustdb.gpg: trustdb created
gpg: key [COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR] marked as ultimately trusted
public and secret key created and signed.

gpg: checking the trustdb
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
gpg: next trustdb check due at 2014-03-06
pub   4096R/[COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR] 2009-03-07 [expires: 2014-03-06]
      Key fingerprint = [COLOR="DarkRed"]**xxxx xxxx xxxx xxxx xxxx  xxxx xxxx xxxx _xxxx xxxx_**[/COLOR]
uid                  Local Ubuntu Intrepid Ibex Repository

Note that this key cannot be used for encryption.  You may want to use
the command "--edit-key" to generate a subkey for this purpose.
```
The bold, underlined and coloured text, [COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR], represents the *"key id"*—which you will have to specify when you export the (*public*) key, next.

**_Note:_**

[INDENT]You can list your keys at any time, with the following command:
```
gpg --list-keys
```
The output will include the *key id,* as shown below:
```
/home/luvr/.gnupg/pubring.gpg
-----------------------------
pub   4096R/[COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR] 2009-03-07 [expires: 2014-03-06]
uid                  Local Ubuntu Intrepid Ibex Repository
```[/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Step 2: Exporting your newly generated Public Key._**[/COLOR][/SIZE]

Now that your GPG key pair is ready, you will have to export the *public* key to a text file, using the following command:
```
gpg --output *pubkey-export-file* --armor --export [COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR]
```
You should, obviously, replace the *pubkey-export-file* parameter string with an appropriate name for the output file. Furthermore, the [COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR] parameter represents the *key id,* as discussed above.

[SIZE="4"][COLOR="DarkRed"]**_Step 3: Importing your Public Key into the APT List of Trusted Keys._**[/COLOR][/SIZE]

**_Note:_**

[INDENT]**You will have to perform this step on every computer on which you want to install software packages from your **(*yet to be created*)** local software repository.**
You can perform this step at any time, and on as many computers as you deem appropriate.[/INDENT]

Make sure that you have the *pubkey-export-file* (which you created in [COLOR="DarkRed"]***Step 2,***[/COLOR] above) available, and execute the following command to import it into the list of keys that will be trusted by APT:
```
sudo apt-key add  *pubkey-export-file*
```
**_Note:_**

[INDENT]To verify if the key was successfully imported into APT, you can run the following command:
```
sudo apt-key list
```
Alternatively, you could start the *"Software Sources"* utility (from the *"System"* &#8594; *"Administration"* menu) and display its *"Authentication"* tab page.
Moreover, you can also start the *"Software Sources"* utility from within the *"Synaptic Package Manager,"* through its *"Settings"* &#8594; *"Repositories"* menu.
[/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Step 4: Installing the *Debian Package Development Tools.*_**[/COLOR][/SIZE]

Return to the computer on which you generated your key pair (i.e., where you ran steps [COLOR="DarkRed"]***1***[/COLOR] and [COLOR="DarkRed"]***2***[/COLOR] above).

Execute the following command to install the *Debian Package Development Tools*:
```
sudo apt-get install dpkg-dev
```
Once this package is installed, you will be able to create software package repositories on this system.

[SIZE="4"][COLOR="DarkRed"]**_Step 5: Creating the Directory Structure for your Local Repository._**[/COLOR][/SIZE]

You will be setting up a *simple* repository—i.e., one that consists of just one directory. Complex repositories, consisting of a deeper directory hierarchy, are out of the scope of this document.

As an example, the following commands will create a *"LocalRepository"* subdirectory under your personal home directory,
```
cd
mkdir LocalRepository
cd LocalRepository
```
(The first *"cd"* command will set your current directory to your home location, after which the second command will create the *"LocalRepository"* subdirectory, and the third command will enter the newly created directory.)

To kickstart your new local repository, you can load it with the software packages that you have recently installed. Whenever you install new software or updates through APT, the required packages will be loaded into the *APT cache*—i.e., the *"/var/cache/apt/archives"* directory on your system. You can now copy these packages to your local repository:
```
cp /var/cache/apt/archives/*.deb .
```
(Notice the lone dot (*"."*) at the end of this command—it is required, and is a placeholder for the *"current directory."* The command effectively copies all Debian packages from the APT cache into your current directory—i.e., into your local repository.)

**_Note:_**

[INDENT]If your APT cache does not contain any packages, then be sure to verify the *"Temporary Files"* setting in the *"Synaptic Package Manager,"* as follows:
[LIST]
[*]Open *"Synaptic Package Manager"* (*"System"* &#8594; *"Administration"* &#8594; *"Synaptic Package Manager"*);
[*]Display its *"Preferences"* dialogue (*"Settings"* &#8594; *"Preferences"*);
[*]Display the *"Files"* tab page;
[*]Under the *"Temporary Files"* header, ensure that either *"Leave all downloaded packages in the cache"* or *"Only delete packages which are no longer available"* is selected.
[/LIST][/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Step 6: Creating the Index File for your Local Repository._**[/COLOR][/SIZE]

Once your local repository contains all the packages that you want to make available through it, you are ready to create the *index* file for the repository. To that end, run the following command:
```
dpkg-scanpackages . /dev/null > Packages
```
This will create a text file, *"Packages,"* which is the plain-text, uncompressed version of the index file. You should also create a compressed version of the index file, using the following command:
```
gzip -9c Packages > Packages.gz
```
This will create the compressed version, *"Packages.gz,"* of the index file, without deleting the original, uncompressed file.

[SIZE="4"][COLOR="DarkRed"]**_Step 7: Creating the Release File for your Local Repository._**[/COLOR][/SIZE]

The *release* file is a small text file that should contain:
[LIST]
[*]A header.
A detailed description of the format of this section is out of the scope of this document, but the following is a simple example of a perfectly valid header:
```
Archive: intrepid
Origin: Ubuntu
Label: Local Ubuntu Intrepid Repository
Architecture: i386
MD5Sum:
```
[*]Two detail lines—one for the uncompressed *"Packages"* file, and one for the compressed  *"Packages.gz"* file. The detail lines should be formatted as follows:
[LIST]
[*]One blank space;
[*]The MD5 checksum for the file, as calculated by the *"md5sum"* command;
[*]One blank space;
[*]The size, in bytes, of the file, right-aligned and padded to the left with blanks, in a 16-character field;
[*]One blank space;
[*]The name of the file.
[/LIST]

The following example shows two valid detail lines:
```
 d8cd948e0371a338025d3d99f5f9f304           454617 Packages
 7e43f7e45a7f49dbb01e659c25997446           109619 Packages.gz
```
[/LIST]
Obviously, it would be an awfully error-prone process if you were to try and manually type in these lines. Hence, an automated process is highly desirable—and, fortunately, not too hard to develop. For example, you can construct the command to generate the detail line for the *"Packages"* file as follows:
[LIST]
[*]To calculate the MD5 checksum, run the *"md5sum"* command:
```
$ **md5sum Packages**
d8cd948e0371a338025d3d99f5f9f304  Packages
```
[*]You should keep only the checksum value, and drop the file name from the output of the *"md5sum"* command. To that end, pipe the output through the *"cut"* command, keeping only the first blank-delimited field:
```
$ **md5sum Packages | cut --delimiter=' ' --fields=1**
d8cd948e0371a338025d3d99f5f9f304
```
[*]To obtain the size of the file, you can use the *"wc"* command with the *"--bytes"* option:
```
$ **wc --bytes Packages**
454617 Packages
```
[*]Again, you need keep only the first blank-delimited field of the output:
```
$ **wc --bytes Packages | cut --delimiter=' ' --fields=1**
454617
```
[*]To generate the properly formatted output line, you can use the *"printf"* command.
The checksum can be inserted directly into the format string thanks to the *"$(...command...)"* construct supported by the shell; for the file size, the format string can specify a 16-character decimal number field, and the value can be given as an argument to be substituted into the format string:
```
$ **printf ' '$(md5sum Packages | cut --delimiter=' ' --fields=1)' %16d Packages\n' \**
> **$(wc --bytes Packages | cut --delimiter=' ' --fields=1)**
 d8cd948e0371a338025d3d99f5f9f304           454617 Packages
```
[/LIST]
Based on the above description, the following is a command sequence to fully automate the creation of the *release* file. To generate the header, a so-called *"here"* document is used--i.e., the input text is copied directly into the command sequence, with a specified marker string (in this case, *"EOF"*) used to mark the end of the document.
```
cat > Release <<EOF
Archive: intrepid
Origin: Ubuntu
Label: Local Ubuntu Intrepid Repository
Architecture: i386
MD5Sum:
EOF
printf ' '$(md5sum Packages | cut --delimiter=' ' --fields=1)' %16d Packages\n' \
   $(wc --bytes Packages | cut --delimiter=' ' --fields=1) >> Release
printf ' '$(md5sum Packages.gz | cut --delimiter=' ' --fields=1)' %16d Packages.gz' \
   $(wc --bytes Packages.gz | cut --delimiter=' ' --fields=1) >> Release
```
[SIZE="4"][COLOR="DarkRed"]**_Step 8: Generating the Digital Signature for the Release File._**[/COLOR][/SIZE]

The digital signature for the *release* file should be written to a file named *"Release.gpg,"* using the following command:
```
gpg --armor --detach-sign --output Release.gpg Release
```
With this step, your local repository is ready for use.

[SIZE="4"][COLOR="DarkRed"]**_Step 9: Adding your Local Repository as an APT Source._**[/COLOR][/SIZE]

Now that your local repository is fully set up, you can copy it to any computer on which you want to use it, and add it to its APT source configuration file, *"/etc/apt/sources.list."*

You will need *root* privileges to edit the *"/etc/apt/sources.list."* file—therefore, if you want to start up your text editor (e.g., *"gedit"*) from a terminal, you should run the command as follows:
```
sudo gedit /etc/apt/sources.list
```
Alternatively, you can start the text editor from the GNOME desktop environment by pressing <Alt>-<F2> to display the *"Run Application*" dialog, and typing the following command:
```
gksudo gedit /etc/apt/sources.list
```
At the top of the file, add a definition for the local repository, as follows:
```
deb   file:///home/luvr/LocalRepository   /
```
(Note that you should, of course, specify the correct path to your repository on the *"file://"* protocol.)

Finally, you should let APT update its internal package index:
```
sudo apt-get update
```
(Alternatively, you can execute the *"Reload"* function in *"Synaptic Package Manager."*)

[SIZE="4"][COLOR="DarkRed"]**_Epilogue: Keeping your Local Repository Up-To-Date._**[/COLOR][/SIZE]

From now on, whenever you perform any further software installations through APT, you should perform the following steps to keep your local repository updated:
[LIST]
[*]Copy the downloaded packages from the APT cache to your local repository;
[*]Recreate the repository *index* and *release* files, and generate a new digital signature.[/LIST]
To fully automate this process, you can execute the *"update-repository"* script file, which you can find attached as a zip archive file to this post.

[SIZE="4"][COLOR="DarkRed"]**_References._**[/COLOR][/SIZE]

[LIST]
[*][How to create a "it really works!" local repository of packages.]("http://ubuntuforums.org/showthread.php?t=263617")
[*][Debian Repository HOWTO.]("http://www.debian.org/doc/manuals/repository-howto/repository-howto")
[*]For a different approach to creating a local repository, see **BobSongs'** tutorial on [How to make your own Ubuntu Repository DVDs.]("http://ubuntuforums.org/showthread.php?t=352460")
For my two cents' worth on how the two methods compare, see [Post #204]("http://ubuntuforums.org/showthread.php?p=6965253#post6965253") of that thread.
Furthermore:
[LIST][*]In [Post #236]("http://ubuntuforums.org/showthread.php?p=7367273#post7367273") of that thread, I explain how to use *"debmirror"* to create a trusted local Ubuntu mirror.
[*]In [Post #243]("http://ubuntuforums.org/showthread.php?p=7455095#post7455095") of that thread, I explain how to create a trusted local Ubuntu mirror from a set of Ubuntu Repository DVDs.[/LIST]
[*][ADDENDUM: Removing Old Package Versions from your Local Repository.]("http://ubuntuforums.org/showthread.php?p=7097305#post7097305") (This is a link to post #12 in this thread.)
[*][ADDENDUM: Installing the "msttcorefonts" Package without Internet Access.]("http://ubuntuforums.org/showthread.php?p=7161462#post7161462") (This is a link to post #17 in this thread.)
[*][ADDENDUM: Transferring your GPG Key Pair to Another Computer.]("http://ubuntuforums.org/showthread.php?p=7205831#post7205831") (This is a link to post #21 in this thread.)
[*][ADDENDUM: Installing the Flash Player Plugin without Internet Access.]("http://ubuntuforums.org/showthread.php?p=9293926#post9293926") (This is a link to post #27 in this thread.)[/LIST]

---

### Post by Mark1959 on 2009-03-22
Thank you for putting together such a clear HOW TO. 

It is so helpful for us noobs to be able to learn by following such instruction. 

Would you be able to clarify the process where one is trying to share the repository on a network ? 

I have three computers sharing using SAMBA both are Ubuntu 8.10 OS and whilst I can easily manually copy the repository to both machines that seems a bit agricultural. 

Should I set up some kind of synchronisation or mirroring of the file systems - this would be good since I could also keep things like books marks consistent between machines. 

Would the better approach be to have the main computer as the central library and address as per step 9;

"At the top of the file, add a definition for the local repository, as follows:
Code:

deb   file:///home/luvr/LocalRepository   /


with an appropriate network address.

I do realize this is a very elementary level of query. It is possible I am attempting this in totally the wrong way. I would be great full for just a pointer in the right direction.

Thank You in Anticipation.

---

### Post by luvr on 2009-03-22
> **Mark1959 said:**
> Would you be able to clarify the process where one is trying to share the repository on a network ? 

I have three computers sharing using SAMBA both are Ubuntu 8.10 OS and whilst I can easily manually copy the repository to both machines that seems a bit agricultural.
To be honest, I haven't given SAMBA much thought so far. In my case, the local repository is particularly useful because I'm trying to keep multiple Ubuntu systems updated that are on different locations, and some of them have rather slow internet connections (I once attempted an update that included a new kernel on one of these, and it took over two hours to download the new package versions!). I'm using a USB disk to transport the contents of my local repository between systems; I do, however, keep local copies of the repository on each machine, and I use the **Unison** file synchronisation tool to ensure that only new and changed files will be copied over whenever I update either the USB disk or the local copies on each of the computers.

Having said that (*and assuming that you have a SAMBA share available that you can access from all of your computers*), you can create your local repository somewhere on the shared directory tree, and specify the path to it in your *sources.list* file--in the very same way that you would specify a repository on a local disk.

For example, if your SAMBA share is mounted at *"/server/samba/share"* and your repository is in directory *"LocalRepository"* within the share, you could simply write:
```
deb   file:///server/samba/share/LocalRepository   /
```
If you want to ensure that the SAMBA share will get automatically mounted whenever you boot up, then you will have to become familiar with the **/etc/fstab** file, in which you will have to specify that the share be automounted. (*Obviously, you will have to ensure that the machine that serves the SAMBA share is up and running, too, since otherwise, the share will not be accessible.*)

> Should I set up some kind of synchronisation or mirroring of the file systems - this would be good since I could also keep things like books marks consistent between machines.
I'm afraid I cannot offer much detailed advice on this, but I believe it should be possible to set up your *"/home"* directory on, e.g., a SAMBA share, and have all of your computers point there for their *"/home"* locations. Then, whichever computer you log on to, you will get the exact same personal settings (from the shared directory). Note that the *"/home"* location will have to be automounted when the system boots, so it will have to be specified in the **/etc/fstab** file (which I hinted at above).

> Would the better approach be to have the main computer as the central library and address as per step 9;

"At the top of the file, add a definition for the local repository, as follows:
```
deb   file:///home/luvr/LocalRepository   /
```
with an appropriate network address.
Whether you set up your local repository on a separate server (e.g., the one that serves your SAMBA share), or on whichever machine that you designate as your *"main"* computer, doesn't really matter--both solutions will work equally well. You could set up a SAMBA share on your *"main"* computer as well, and work from there.

There's also the option of setting up an HTTP or FTP repository on your local network, but I haven't looked into these features yet, and I cannot really tell you much more about them.

I hope this answers at least *some* of your questions, or that it offers you the right pointers to get you started.

---

### Post by Geochelone on 2009-03-25
How to make apt prefer this trusted local repositories instead of Internet? When I disable my network, apt will get the packages from local repo, which is ultra snappy.

However, when I enable my network, apt will get the packages from Internet, instead of local repo.

For example, I want to install restricted extras. When network is disabled, installation is blazing fast, however without flash player and ms core fonts. When network is enabled, installation is slow (as apt downloads the packages from Internet).

Thus, how to make apt to fetch packages from local repo, unless the packages aren't available locally?

---

### Post by luvr on 2009-03-25
> **Geochelone said:**
> How to make apt prefer this trusted local repositories instead of Internet?
First, you will have to ensure that your *public key* was successfully imported into the APT list of public keys on the computer where you want to use the repository. (If it wasn't, then you will get some warning to the effect that the digital signature could not be verified.)

Next, ensure that the local repository was added to the */etc/apt/sources.list* file on the computer. Also make sure, however, that the *local* repository is specified **first;** if the system finds the same package in multiple places (e.g., once in your local repository, and once in a repository on the internet), it will load it from the **first** location in the *sources.list* file where it finds the package. In other words, if the internet repository is specified *before* the local repository in *sources.list,* then the internet repository will be preferred; the local repository will be used only if the system cannot access the internet repository.

---

### Post by luvr on 2009-03-28
> **Geochelone said:**
> flash player and ms core fonts.
This is a little detail that I missed upon first reading of your reply.

I'm not sure about Flash Player, but the **msttcorefonts** package will download its font files from the internet when you install it; these files are not integrated into the package itself. That's why, even if the package itself gets installed from a local repository, it will still download a bunch of files from the internet. I'm sure there must be a way to install the fonts from local copies of the font files, but I haven't looked into this issue deeply enough to understand how exactly it would be done.

---

### Post by BobSongs on 2009-03-28
**luvr**: I've added your tutorial as a cross reference on my tutorial. I like the topic (closely related) and particularly the patience in your layout and writing. I hope we can point to each other's tutorials as long as they continue here.

Bob

---

### Post by luvr on 2009-03-29
I found more information on:
> **Geochelone said:**
> flash player and ms core fonts.
Specifically, how to install the Microsoft TrueType Core Fonts on a computer that has no access to the internet: [msttcorefonts on standalone machine.]("http://ubuntuforums.org/showpost.php?p=1186473&postcount=2")

---

### Post by Geochelone on 2009-04-10
Oh hay!

I'm trying to make the bash script run-able from anywhere in my laptop. So I mod it here and there. And I hit some bumps.

Here is the modded script.

```
#!/bin/sh
# DECLARE
L1=/media/Tortoise/Repositories/Jaunty/Canonical
#*******************************************************************************************************************************
#*                                                                                                                             *
#* Generate the "Packages" index file.                                                                                         *
#*                                                                                                                             *
#*******************************************************************************************************************************
dpkg-scanpackages $L1 /dev/null > $L1/Packages
#*******************************************************************************************************************************
#*                                                                                                                             *
#* Create the "Packages.gz" compressed index file.                                                                             *
#*                                                                                                                             *
#*******************************************************************************************************************************
gzip -9c $L1/Packages > $L1/Packages.gz
#*******************************************************************************************************************************
#*                                                                                                                             *
#* Create the "Release" file.                                                                                                  *
#*                                                                                                                             *
#*******************************************************************************************************************************
cat > Release <<EOF
Archive: Intrepid
Origin: Ubuntu
Label: Official
Architecture: i386
MD5Sum:
EOF
printf ' '$(md5sum $L1/Packages    | cut --delimiter=' ' --fields=1)' %16d /media/Tortoise/Repositories/Jaunty/Canonical/Packages\n'  $(wc --bytes $L1/Packages    | cut --delimiter=' ' --fields=1) >> $L1/Release
printf ' '$(md5sum $L1/Packages.gz | cut --delimiter=' ' --fields=1)' %16d /media/Tortoise/Repositories/Jaunty/Canonical/Packages.gz' $(wc --bytes $L1/Packages.gz | cut --delimiter=' ' --fields=1) >> $L1/Release
```

The resultant *Release* file is different from the original script. It misses the MD5Sum part.

Could you please show me where is wrong and why?

PS: /media/Tortoise/ is my portable hard disk. I intend to run the script from my home folder.

---

### Post by luvr on 2009-04-14
> **Geochelone said:**
> The resultant *Release* file is different from the original script. It misses the MD5Sum part.

Could you please show me where is wrong and why?

Looks to me like you're writing the header lines (i.e., the output of the *"cat"* command) into a different file from the detail lines (i.e., the output of the *"printf"* commands). Indeed, your *"cat"* command specifies just ***"Release"*** as its output file:
```
cat > **Release** <<EOF
```
On the *"printf"* commands, on the other hand, you specify  ***"$L1/Release"*** for the output file:
```
printf *...dadododah...* >> **$L1/Release**
```
Your problem will likely get solved if you change the output file name on the *"cat"* command to **$L1/Release**--the same as on the *"printf"* commands.

---

### Post by Geochelone on 2009-04-15
luvr, thank you :-) You are correct, I missed that part. Once I changed Release to $L1, it worked as expected. Thanks!

---

### Post by luvr on 2009-04-18
[SIZE="4"][COLOR="DarkRed"]**_The Problem._**[/COLOR][/SIZE]

After you created your local repository, you keep updating it by copying ever newer package versions into it. The old versions of the packages, however, never get removed from the repository. As a result, whenever you regenerate its index file, you get tons of warning messages such as the following:
```
 ! Package firefox-3.0 (filename ./firefox-3.0_3.0.8+nobinonly-0ubuntu0.8.10.2_i386.deb) is repeat but newer version;
   used that one and ignored data from ./firefox-3.0_3.0.5+nobinonly-0ubuntu0.8.10.1_i386.deb !
 ! Package firefox-gnome-support (filename ./firefox-gnome-support_3.0.7+nobinonly-0ubuntu0.8.10.1_all.deb) is repeat;
   ignored that one and using data from ./firefox-gnome-support_3.0.8+nobinonly-0ubuntu0.8.10.2_all.deb !
```
In this post, I present a quick'n'dirty hack to allow you to remove the old packages from the repository, in order to eliminate these warnings. As an added benefit, your repository will get cleaned up, and the space that was taken up by the old packages will be freed up.

[SIZE="4"][COLOR="DarkRed"]**_A Fair Warning._**[/COLOR][/SIZE]

The hack that I present here *seems* to work, but I developed it as a patch to the *”dpkg-scanpackages”* Perl script, which, admittedly, I hardly understand. I simply searched for the places where the script generated the warning messages, and inserted what I assume to be the appropriate print statements in what I assume to be the appropriate places. In addition, I deleted quite a bit of code from the end of the script, because it seemed to be unnecessary for my purposes.

I **did** test my patched script on my *simple* repository, and it works fine there; I don't know, however, if it would work equally well on a *complex* repository. Try it at your own risk!

[SIZE="4"][COLOR="DarkRed"]**_A Warning about *debmirror.*_**[/COLOR][/SIZE]

[B]_Warning:_
[INDENT]If you use *debmirror* to maintain a local repository, then you really should *_not_* perform any manual maintenance on your local copy.[/INDENT]
_Note:_[/B]
[INDENT]For information on the use of *debmirror,* see [*"How to make your own Ubuntu Repository DVDs,"*]("http://ubuntuforums.org/showthread.php?t=352460") posted by **BobSongs.**[/INDENT]

The online repositories will generally keep a number of old package versions available for a while. If you *manually* delete these, and you subsequently run *debmirror* to bring your local repository up-to-date again, then *debmirror* will notice that they are missing from your local copy, and *redownload* them (since it wants to bring your local repository fully in sync with the online version).

You should really leave it up to *debmirror* to maintain your local repository; once the old package versions are removed from the online repository, the next time you run *debmirror,* they will be deleted from your local repository as well.

*(Thanks to **Geochelone** for reporting this issue--cfr. [Post #18]("http://ubuntuforums.org/showpost.php?p=7189312&postcount=18") in this thread.)*

[SIZE="4"][COLOR="DarkRed"]**_Preparing for the Patch._**[/COLOR][/SIZE]

The *”dpkg-scanpackages”* Perl script, which I used as the basis for my patch, should be located in your */usr/bin* directory. I didn't, of course, want to mess with this existing script, so I decided to create a copy under a new name, and hack that copy. I used *”gen-deloldpackages”* as the name for my patched script; if you want to apply the patch as I attached it to this post, you will have to create your copy under the same name—e.g., in your home directory—with the following commands:
```
cd
cp /usr/bin/dpkg-scanpackages gen-deloldpackages
```
**_Note:_**
[INDENT]I developed the patch on version *1.14.20ubuntu1* of the *"dpkg-scanpackages"* script under Ubuntu 8.10 (*"the Intrepid Ibex"*)—which is apparently identical to version *1.14.24ubuntu1* of the script under Ubuntu 9.04 (*"the Jaunty Jackalope"*). If you use any other version of the script, then the patch may or may not work right.
To verify the *"dpkg-scanpackages"* version on your system, you can simply run the following command:
```
dpkg-scanpackages --version
```
If you're running Ubuntu 8.10, the output should look like this:
```
Debian dpkg-scanpackages version 1.14.20ubuntu1.
```
Under Ubuntu 9.04, on the other hand, the output should look like this:
```
Debian dpkg-scanpackages version 1.14.24ubuntu1.
```[/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Applying the Patch._**[/COLOR][/SIZE]

Download the *”patch_gen-deloldpackages.zip”* file attached to this post. Save it into your home directory (or wherever you created the *”gen-deloldpackages”* file in the first place), and run the following command to unzip it:
```
unzip patch_gen-deloldpackages.zip
```
This will create the *”patch_gen-deloldpackages”* file—which you can use to apply the patch, as follows:
```
patch < patch_gen-deloldpackages
```
Just to be sure, you may want to verify that the patched script file is *executable*—i.e., that you can run it as a shell command; to this end, enter the following command:
```
ls -l gen-deloldpackages
```
The output should look something like this:
```
-rw[COLOR="DarkRed"]**x**[/COLOR]r-[COLOR="DarkRed"]**x**[/COLOR]r-[COLOR="DarkRed"]**x**[/COLOR] 1 luvr luvr 6588 2009-04-18 23:38 gen-deloldpackages
```
In particular, the three [COLOR="DarkRed"]**”x”**[/COLOR] characters that I highlighted in the output should be present; if they aren't, then you should use the folllowing command to set them:
```
chmod +x gen-deloldpackages
```
Then, rerun the *”ls”* command, above, to be absolutely, positively sure.

[SIZE="4"][COLOR="DarkRed"]**_Testing the Patched Script._**[/COLOR][/SIZE]

The patched script works somewhat similar to the original, *”dpkg-scanpackages,”* except that it won't actually create a new index file. To test it, enter the directory in which you set up your local repository, and run the folllowing command:
```
~/gen-deloldpackages . /dev/null
```
**_Note:_**
[INDENT]The *”~/”* that are prepended to the name of the script, indicate that the file is located in your home directory. If you stored the script in any other location, you will have to modify the path accordingly.[/INDENT]
You should see the very same warnings that you got from the *”dpkg-scanpackages”* command, but every warning should be followed by a line that begins with **”rm”**—e.g.:
```
 ! Package firefox-3.0 (filename ./firefox-3.0_3.0.8+nobinonly-0ubuntu0.8.10.2_i386.deb) is repeat but newer version;
   used that one and ignored data from ./firefox-3.0_3.0.5+nobinonly-0ubuntu0.8.10.1_i386.deb !
rm './firefox-3.0_3.0.5+nobinonly-0ubuntu0.8.10.1_i386.deb'
 ! Package firefox-gnome-support (filename ./firefox-gnome-support_3.0.7+nobinonly-0ubuntu0.8.10.1_all.deb) is repeat;
   ignored that one and using data from ./firefox-gnome-support_3.0.8+nobinonly-0ubuntu0.8.10.2_all.deb !
rm './firefox-gnome-support_3.0.7+nobinonly-0ubuntu0.8.10.1_all.deb'
```
The **”rm”** lines are the commands to *remove* the old packages; if you want to execute the script for real, you will want to catch these lines into a genuine file, and execute that as a shell script—as described next.

[SIZE="4"][COLOR="DarkRed"]**_Executing the Patched Script for Real._**[/COLOR][/SIZE]

The **”rm”** lines that the patched script generates, are output to the *”standard output”* stream, while the warning messages go to *”standard error.”* Thus, if you redirect *”standard output”* to a file, these **”rm”** lines will go there, while the warnings will still be displayed on screen—e.g., the following command will send the **”rm”** lines to a file named *”deloldpkgs”*:
```
~/gen-deloldpackages . /dev/null > deloldpkgs
```
**_Note:_**
[INDENT]If you prefer to suppress the warning messages, then you can additionally redirect *”standard error”* to *”/dev/null,”* as follows:
```
~/gen-deloldpackages . /dev/null > deloldpkgs 2> /dev/null
```[/INDENT]
Now that the list of *”remove”* commands is present in a file, you will want to run that file in order to actually execute the commands—i.e., to delete the old package files. To that end, you could make the *”deloldpkgs”* file *executable* (just like you may have had to do with the *”gen-deloldpackages”* before), and then run it—e.g.:
```
chmod +x deloldpkgs
./deloldpkgs
```
As an alternative, though, you could simply *”source”* the file into your shell session, using the *”.”* (i.e, simply a dot) command, as follows:
```
. deloldpkgs
```
**_Note:_**
[INDENT]The *”.”* (dot) command is really just a shorthand for the *”source”* command. The following will, therefore, work equally well:
```
source deloldpkgs
```[/INDENT]
Either way, once the *”deloldpkgs”* file finishes, the old packages should have disappeared from your repository.

**_Tip:_**
[INDENT]Instead of writing the list of *"remove"* commands to an actual file, and subsequently executing them in a separate step, you may pipe the output of the *"gen-deloldpackages"* into a standard shell, as follows:
```
~/gen-deloldpackages . /dev/null 2> /dev/null | sh
```
This combines the generation of the command list, and its subsequent execution, into a single step; as an added bonus, it also eliminates the need for the intermediate file.[/INDENT]

---

### Post by k3lt01 on 2009-04-18
Hi luvr. I have only just seen this thread after checking BobSongs thread for updates.

If I may make 1 comment on what you are trying to do, with regards to the OP, have you seen this? [Apt-Catcher-Server]("https://help.ubuntu.com/community/Apt-Cacher-Server"). To me it does exactly what you initially wanted to do. After I finish setting up my home server/network it is what I plan to do.

---

### Post by luvr on 2009-04-19
> **k3lt01 said:**
> [Apt-Catcher-Server]("https://help.ubuntu.com/community/Apt-Cacher-Server")
Thanks for the link--I think I'll look into it for Jaunty, when that is released in a few days.

---

### Post by j.crilly on 2009-04-23
Is it possible to change the default location that Ubuntu stores the deb files from /var/cache/apt/archives/ to say /media/Elements/repos?

This would save copying the files...

---

### Post by luvr on 2009-04-24
> **j.crilly said:**
> Is it possible to change the default location that Ubuntu stores the deb files from /var/cache/apt/archives/ to say /media/Elements/repos?

This would save copying the files...
I'm not sure whether or not there's an option to change the location of the APT cache, but even so, I don't think that it would be a good idea to use that location directly for your local repository. The APT system removes files from its cache from time to time, so you really cannot use it as a reliable repository.

Having said that, copying the files to your local repository can be as simple as running the following command:
```
cp --update --verbose /var/cache/apt/archives/*.deb */your/local/repository*
```
(which copies only new and updated debian package files to your local repository--you could even abbreviate the *"--update"* option to *"-u"* and remove the *"--verbose"* option, if you want to shorten the command).

Just add this command to the top of the *"update-repository"* script, and it will be automatically executed whenever you update your local repository.

***Note:***

[INDENT]I attached an updated version of the *"update-repository"* script to the original post. It now includes the command to copy the new debian package files to the local repository.[/INDENT]

---

### Post by luvr on 2009-04-27
[SIZE="4"][COLOR="DarkRed"]**_The Problem._**[/COLOR][/SIZE]

You successfully installed the *“Microsoft TrueType core fonts”* software package (i.e., *“msttcorefonts”*) on one computer that has full internet access, and you are making the package available locally—e.g., through a local software repository.

You are now trying to install the package on another computer, but this time with limited or no internet access, e.g., with the following command:
```
sudo apt-get install msttcorefonts
```

When the command starts up, it produces the following output:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  cabextract ttf-liberation ttf-mscorefonts-installer
The following NEW packages will be installed:
  cabextract msttcorefonts ttf-liberation ttf-mscorefonts-installer
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1101kB of archives.
After this operation, 2159kB of additional disk space will be used.
Do you want to continue [Y/n]?
```
You notice, specifically, the line that reads ***“Need to get 0B/1101kB of archives.”*** From this output line, you draw the conclusion that the software packages will *not* be downloaded from the internet, but that the files that you want to install, will be taken from your local repository instead.

However, when you continue the operation, you discover that the installer still attempts to download a set of Microsoft Windows executable (*“.exe”*) files from SourceForge; these downloads will, obviously, fail if the computer does not have an active internet connection—e.g.:
```
--2009-04-27 15:27:13--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving surfnet.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `surfnet.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `heanet.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `nchc.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internap.dl.sourceforge.net'
--2009-04-27 15:27:13--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `switch.dl.sourceforge.net'
```
In this post, I will explain why this problem is happening, and how to work around it.

[SIZE="4"][COLOR="DarkRed"]**_Why is this Problem Happening?_**[/COLOR][/SIZE]

The reason why the Microsoft Windows executable files have to be separately downloaded, is uncovered by a notice that is shown to you when you attempt to install the *“msttcorefonts”* software package:
```
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
```
The key to the problem is the phrase that ***“you may not redistribute them in modified form, [COLOR="DarkRed"]including changes to the file name or packaging format.[/COLOR]"***
In other words, since the files are distributed as *“.exe”* files, you are **not** allowed to provide them in any other format. In particular, you should **not** include them in a Debian *(or, for that matter, an RPM)* software package. You will, therefore, have to provide them, *unchanged,* as separate files to any software installation mechanism through which you want to make them available.

[SIZE="4"][COLOR="DarkRed"]**_What happens to the Files after they are Downloaded?_**[/COLOR][/SIZE]

When you install the *“msttcorefonts”* software package, and you let it run to completion, it takes roughly the following steps:
[LIST]
[*]It downloads the Microsoft Windows executable files from SourceForge to a temporary directory on the local computer;
[*]It extracts the TrueType font definition (*“.ttf”*) files from the downloaded executables, and saves them into an appropriate permanent location;
[*]It takes any further actions required to make the newly installed fonts available to the font rendering subsystem, and to mark the package as being successfully installed.
[/LIST]
Fortunately, the *“msttcorefonts”* package has some basic intelligence built into it: Before it decides to download the executables, it will verify if, perhaps, the font definition (*“.ttf”*) files are already present in the expected permanent location; if it finds the files there, then it will not redownload or reinstall them. To avoid having to download them during the installation of the package, you should, therefore, *manually* copy them to the appropriate location **before** you actually install the package.

The remainder of this document will explain how you can copy the font files into a typical archive file, from which you can subsequently retrieve them, very easily and quickly, on any computer on which you want to install them.

**_Important:_**

[INDENT]Keep in mind that, according to their usage terms, *you are **not allowed** to distribute the fonts in any form **except** as the original, unmodified Microsoft Windows executable files.* You should not, therefore, send the archive file that you are about to create, to anyone else, but you *may* explain to them how they can create their own copy of the archive—just as I am doing here.[/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Step 1: Creating an Archive from the Font Files._**[/COLOR][/SIZE]

**_Note:_**

[INDENT]You should execute this step on a computer on which you have already installed the *“Microsoft TrueType core fonts”* software package.[/INDENT]

When you install the*“msttcorefonts”* package, the font files will get copied to the *“/usr/share/fonts/truetype/msttcorefonts”* directory. To verify if they are really there, you can run the following command:
```
ls -l /usr/share/fonts/truetype/msttcorefonts
```
You should get a listing like the following:
```
total 5704
-rw-r--r-- 1 root root 105468 1998-11-12 07:18 Andale_Mono.ttf
lrwxrwxrwx 1 root root     15 2009-02-23 20:04 andalemo.ttf -> Andale_Mono.ttf
lrwxrwxrwx 1 root root     14 2009-02-23 20:04 arialbd.ttf -> Arial_Bold.ttf
lrwxrwxrwx 1 root root     21 2009-02-23 20:04 arialbi.ttf -> Arial_Bold_Italic.ttf
-rw-r--r-- 1 root root 117028 1998-11-10 13:52 Arial_Black.ttf
-rw-r--r-- 1 root root 224692 2000-05-11 11:45 Arial_Bold_Italic.ttf
-rw-r--r-- 1 root root 286620 2000-05-11 11:45 Arial_Bold.ttf
-rw-r--r-- 1 root root 206132 2000-05-11 11:45 Arial_Italic.ttf
lrwxrwxrwx 1 root root     16 2009-02-23 20:04 ariali.ttf -> Arial_Italic.ttf
lrwxrwxrwx 1 root root      9 2009-02-23 20:04 arial.ttf -> Arial.ttf
-rw-r--r-- 1 root root 275572 2000-05-11 11:45 Arial.ttf
lrwxrwxrwx 1 root root     15 2009-02-23 20:04 ariblk.ttf -> Arial_Black.ttf
lrwxrwxrwx 1 root root     22 2009-02-23 20:04 comicbd.ttf -> Comic_Sans_MS_Bold.ttf
-rw-r--r-- 1 root root 111476 1998-11-10 13:52 Comic_Sans_MS_Bold.ttf
-rw-r--r-- 1 root root 126364 1998-11-10 13:52 Comic_Sans_MS.ttf
lrwxrwxrwx 1 root root     17 2009-02-23 20:04 comic.ttf -> Comic_Sans_MS.ttf
lrwxrwxrwx 1 root root     20 2009-02-23 20:04 courbd.ttf -> Courier_New_Bold.ttf
lrwxrwxrwx 1 root root     27 2009-02-23 20:04 courbi.ttf -> Courier_New_Bold_Italic.ttf
-rw-r--r-- 1 root root 234788 2000-05-11 11:45 Courier_New_Bold_Italic.ttf
-rw-r--r-- 1 root root 311508 2000-05-11 11:45 Courier_New_Bold.ttf
-rw-r--r-- 1 root root 244156 2000-05-11 11:45 Courier_New_Italic.ttf
-rw-r--r-- 1 root root 302688 2000-05-11 11:45 Courier_New.ttf
lrwxrwxrwx 1 root root     22 2009-02-23 20:04 couri.ttf -> Courier_New_Italic.ttf
lrwxrwxrwx 1 root root     15 2009-02-23 20:04 cour.ttf -> Courier_New.ttf
-rw-r--r-- 1 root root 158796 1998-11-10 14:00 Georgia_Bold_Italic.ttf
-rw-r--r-- 1 root root 139584 1998-11-10 14:00 Georgia_Bold.ttf
lrwxrwxrwx 1 root root     16 2009-02-23 20:04 georgiab.ttf -> Georgia_Bold.ttf
-rw-r--r-- 1 root root 156668 1998-11-10 14:00 Georgia_Italic.ttf
lrwxrwxrwx 1 root root     18 2009-02-23 20:04 georgiai.ttf -> Georgia_Italic.ttf
lrwxrwxrwx 1 root root     11 2009-02-23 20:04 georgia.ttf -> Georgia.ttf
-rw-r--r-- 1 root root 142964 1998-11-10 13:59 Georgia.ttf
lrwxrwxrwx 1 root root     23 2009-02-23 20:04 georgiaz.ttf -> Georgia_Bold_Italic.ttf
lrwxrwxrwx 1 root root     10 2009-02-23 20:04 impact.ttf -> Impact.ttf
-rw-r--r-- 1 root root 136076 1998-11-10 13:52 Impact.ttf
lrwxrwxrwx 1 root root     24 2009-02-23 20:04 timesbd.ttf -> Times_New_Roman_Bold.ttf
lrwxrwxrwx 1 root root     31 2009-02-23 20:04 timesbi.ttf -> Times_New_Roman_Bold_Italic.ttf
lrwxrwxrwx 1 root root     26 2009-02-23 20:04 timesi.ttf -> Times_New_Roman_Italic.ttf
-rw-r--r-- 1 root root 238612 2000-05-11 11:45 Times_New_Roman_Bold_Italic.ttf
-rw-r--r-- 1 root root 333900 2000-05-11 11:45 Times_New_Roman_Bold.ttf
-rw-r--r-- 1 root root 247092 2000-05-11 11:45 Times_New_Roman_Italic.ttf
-rw-r--r-- 1 root root 330412 2000-05-11 11:45 Times_New_Roman.ttf
lrwxrwxrwx 1 root root     19 2009-02-23 20:04 times.ttf -> Times_New_Roman.ttf
lrwxrwxrwx 1 root root     21 2009-02-23 20:04 trebucbd.ttf -> Trebuchet_MS_Bold.ttf
lrwxrwxrwx 1 root root     28 2009-02-23 20:04 trebucbi.ttf -> Trebuchet_MS_Bold_Italic.ttf
-rw-r--r-- 1 root root 131188 2001-04-09 16:05 Trebuchet_MS_Bold_Italic.ttf
-rw-r--r-- 1 root root 123828 2001-04-09 16:05 Trebuchet_MS_Bold.ttf
-rw-r--r-- 1 root root 139288 2001-04-09 16:05 Trebuchet_MS_Italic.ttf
-rw-r--r-- 1 root root 126796 2001-04-09 16:05 Trebuchet_MS.ttf
lrwxrwxrwx 1 root root     23 2009-02-23 20:04 trebucit.ttf -> Trebuchet_MS_Italic.ttf
lrwxrwxrwx 1 root root     16 2009-02-23 20:04 trebuc.ttf -> Trebuchet_MS.ttf
-rw-r--r-- 1 root root 153324 1998-11-12 07:18 Verdana_Bold_Italic.ttf
-rw-r--r-- 1 root root 136032 1998-11-12 12:15 Verdana_Bold.ttf
lrwxrwxrwx 1 root root     16 2009-02-23 20:04 verdanab.ttf -> Verdana_Bold.ttf
-rw-r--r-- 1 root root 154264 1998-11-12 07:18 Verdana_Italic.ttf
lrwxrwxrwx 1 root root     18 2009-02-23 20:04 verdanai.ttf -> Verdana_Italic.ttf
lrwxrwxrwx 1 root root     11 2009-02-23 20:04 verdana.ttf -> Verdana.ttf
-rw-r--r-- 1 root root 139640 1998-11-12 07:18 Verdana.ttf
lrwxrwxrwx 1 root root     23 2009-02-23 20:04 verdanaz.ttf -> Verdana_Bold_Italic.ttf
lrwxrwxrwx 1 root root     12 2009-02-23 20:04 webdings.ttf -> Webdings.ttf
-rw-r--r-- 1 root root 118752 1998-07-10 08:47 Webdings.ttf
```

To store these files into a *“gzipped tar”* archive file, you can execute the following command:
```
tar --create --verbose --gzip --absolute-names --file msttcorefonts.tar.gz /usr/share/fonts/truetype/msttcorefonts
```
This will run the *“tar”* program with the following parameters:
[LIST]
[*]**“--create”**—Create a new archive file.
This option may be abbreviated to *“-c”.*
[*]**“--verbose”**—List the files as they are processed.
This option may be abbreviated to *“-v”*; without it, the program will run quietly.
[*]**“--gzip”**—Create a compressed archive, using the *“gzip”* utility.
This option may be abbreviated to *“-z”*; without it, the archive will not be compressed—which is not recommended.
As an alternative, you may use the *“--bzip2”* (or *“-j”*) option instead—which will generally create slightly smaller archives, but take longer to complete.
[*]**“--absolute-names”**—Record absolute path names for the stored files, including leading *“/”* characters.
This option may be abbreviated to *“-P”* (i.e., *uppercase* “P”); without it, the leading *“/”* characters will be omitted, and the files will be stored with *relative* paths instead.
[*]**“--file msttcorefonts.tar.gz”**—This option specifies the name of the archive file that will be created.
This option may be abbreviated to *“-f msttcorefonts.tar.gz”*.
If you use *gzip* compression, then you should generally specify *“.tar.gz”* (or *“.tgz”*) as the filename extension.
Alternatively, for *bzip2* compression, *“.tar.bz2”* is the generally recognised extension.
[*]Finally, one or more paths must be given, which identify the files and/or directories that you want to archive.
[/LIST]
**_Note:_**

[INDENT]The command line as shown above, uses *long option names,* which are, admittedly, somewhat uncommon. The following is an equivalent, abbreviated command—which you will likely encounter much more frequently:
```
tar -cvzPf msttcorefonts.tar.gz /usr/share/fonts/truetype/msttcorefonts
```[/INDENT]

To verify if the archive file was created correctly, you can run the *“tar”* command with the *“--list”* (or *“-t”*) option—i.e.:
```
tar --list --verbose --gzip --absolute-names --file msttcorefonts.tar.gz
```
or, in its abbreviated form:
```
tar -tvzPf msttcorefonts.tar.gz
```

[SIZE="4"][COLOR="DarkRed"]**_Step 2: Extracting the Font Files from the Archive._**[/COLOR][/SIZE]

You can now use the *“msttcorefonts.tar.gz”* archive file, created above, to copy the font files to their proper location onto any computer on which you want to install the *“Microsoft TrueType core fonts”* package. Just run the following command in order to extract the contents of the archive:
```
sudo tar --extract --verbose --gzip --absolute-names --file msttcorefonts.tar.gz
```
or, in its abbreviated form:
```
sudo tar -xvzPf msttcorefonts.tar.gz
```

Note that you will have to run this command under the all-powerful *“root”* user account (i.e., via *“sudo”*), because it will need *write* permission to the *“/usr/share/fonts/truetype/msttcorefonts”* location—which is a system directory.

Also, make sure to include the *“--absolute-names”* (or *“-P”*) option; if you omit it, then the leading *“/”* characters on the target path names will be ignored, and the files will be extracted into a *“usr”* subdirectory of whichever location happens to be your current working directory.

[SIZE="4"][COLOR="DarkRed"]**_Step 3: Installing the *“msttcorefonts”* Package._**[/COLOR][/SIZE]

Now that the actual font files are available on the target computer, they will not be downloaded again when you install the *“msttcorefonts”* package, e.g., with the following command:
```
sudo apt-get install msttcorefonts
```

No data will need to be downloaded, but the following line will appear as part of the output from the installation process:
```
All fonts downloaded and installed.
```

Once the installation procedure is completed, the *Microsoft TrueType core fonts* will be available for use on the computer.

---

### Post by Geochelone on 2009-05-01
Hi luvr,

**This section of the thread is referred: ***ADDENDUM: Removing Old Package Versions from your Local Repository.*

I used to employ this hack and slash trick to clear the dupes from my Intrepid repo (Canonical, MediBuntu and Official). However, when I run debmirror after I cleared the dupes, it said I need to download XXX MB of packages.

I found out those XXX MB of packages are actually the dupes I deleted earlier. 

*

I copy the outputs of the dpkg-scanpackages, e.g.

```
! Package cupsys-common (filename /home/geochelone/Desktop/Repositories/Jaunty/Official/pool/universe/c/cups/cupsys-common_1.3.9-17ubuntu2_all.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Jaunty/Official/pool/universe/c/cups/cupsys-common_1.3.9-17ubuntu1_all.deb !
! Package libcupsys2 (filename /home/geochelone/Desktop/Repositories/Jaunty/Official/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu2_all.deb) is repeat but newer version;
   used that one and ignored data from /home/geochelone/Desktop/Repositories/Jaunty/Official/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu1_all.deb !
```

I copied the all the ignored packages, and > them to a file.

```
/home/geochelone/Desktop/Repositories/Jaunty/Official/pool/universe/c/cups/cupsys-common_1.3.9-17ubuntu1_all.deb
/home/geochelone/Desktop/Repositories/Jaunty/Official/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu1_all.deb
```

Then, I just rm the dupes from the list inside the file.

*

Idk what's wrong.

---

### Post by luvr on 2009-05-01
> **Geochelone said:**
> I used to employ this hack and slash trick to clear the dupes from my Intrepid repo (Canonical, MediBuntu and Official). However, when I run debmirror after I cleared the dupes, it said I need to download XXX MB of packages.

I found out those XXX MB of packages are actually the dupes I deleted earlier.
Well--it looks like this is an issue that I had overlooked. I haven't used *debmirror* yet, so I didn't run into this problem myself.

I guess that the online repositories keep a number of old packages available for a while. Now, if you delete them from your local repository, then *debmirror* will notice that these old versions are available online, but that you do not have them in your local copy. Therefore, since *debmirror* wants to synchronise your local copy with the online repository, it will redownload these absent files.

Conversely, if a file is available *locally,* but is missing in the online repositories, then *debmirror* will assume that it is no longer available online, and that it must be deleted from the local copy.

The moral of the story, then, appears to be, that you should **not** manually remove files from (or add files to) a local repository that you maintain via *debmirror.* Instead, you should leave all maintenance of the local copy up to *debmirror.*

I'll add a note about this issue to my post, since it **is** something to be aware of.

---

### Post by Geochelone on 2009-05-01
I believe so too.

However, your tips should work very well to maintain downloaded packages from PPA.

Thanks for the tips!

---

### Post by luvr on 2009-05-03
[SIZE="4"][COLOR="DarkRed"]**_Abstract._**[/COLOR][/SIZE]

You generated a *GPG key pair* that you use to maintain a trusted local repository. Since the *private* (or *“secret”*) key part is available only on the computer on which you generated the key pair, you can create the digital signature for the repository only on that one computer.

Even though, generally, you should not distribute the secret key to multiple computers, you may occasionally want to transfer it, e.g., when you replace your current computer with a new one.

[SIZE="4"][COLOR="DarkRed"]**_Step 1: Exporting your GPG Key Pair._**[/COLOR][/SIZE]

To export your GPG key pair, you will have to export both the *public* and the *private* key parts. You have already exported the *public* key, in [COLOR="DarkRed"]***Step 2***[/COLOR] of the initial post of this thread. If you still have the export file available, you may reuse it now; otherwise, just rerun the following command to export the public key to a text file again:
```
gpg --output *pubkey-export-file* --armor --export [COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR]
```
Again, replace the *pubkey-export-file* parameter string with an appropriate name for the output file, and replace the [COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR] parameter with the *key id.*

[INDENT]**_Note:_**

[INDENT]Remember that you can list your keys at any time, with the following command:
```
gpg --list-keys
```
The output will include the *key id,* as shown below:
```
/home/luvr/.gnupg/pubring.gpg
-----------------------------
pub   4096R/[COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR] 2009-03-07 [expires: 2014-03-06]
uid                  Local Ubuntu Intrepid Ibex Repository
```[/INDENT][/INDENT]

Next, execute the following command to export the *private* key to a text file:
```
gpg --output *seckey-export-file* --armor --export-secret-key [COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR]
```

**_Warning:_**

[INDENT]Keep in mind that the *private* key should be kept secret. Therefore, you should **delete** any copies of the export file as soon as you no longer need them—or, at least, keep them in a **very, *very*** safe place indeed.[/INDENT]

After you exported both the *public* and the *private* key parts, you can transfer the resulting text files to your new computer, where you can subsequently import them—as described next.

[SIZE="4"][COLOR="DarkRed"]**_Step 2: Importing your GPG Key Pair on Your New Computer._**[/COLOR][/SIZE]

Once the *pubkey-export-file* and the *seckey-export-file* are available on your new computer, you are ready to import them into its keyring.

To import the *public* key part, run the following command:
```
gpg --import *pubkey-export-file*
```

Then, to import the *private* key part, run the following command:
```
gpg --allow-secret-key-import --import *seckey-export-file*
```
Your key pair is now available on your new computer; you may want to list your keys, as documented above, to verify this.

Remember that, to be safe, you should now **delete** the *seckey-export-file* (to which you exported the *private* key part).

[SIZE="4"][COLOR="DarkRed"]**_Appendix A: Changing the Passphrase of the Secret Key._**[/COLOR][/SIZE]

You can change the *passphrase* of the *private* key part, as documented next.

**_Note:_**

[INDENT]Even though you will be working at the command line to complete this procedure (as well as the one documented in [COLOR="DarkRed"]***Appendix B,***[/COLOR] below), the system may at times pop up a dialog box to ask for your passphrase. If, like me, you find this behaviour rather annoying and potentially confusing or distracting, you can prevent this dialog box from appearing, as follows:
[LIST]
[*]Start the *“Encryption and Keyrings”* utility (*“System”* &#8594; *“Preferences”* &#8594; *“Encryption and Keyrings”*);
[*]Select the *“PGP Passphrases”* tab;
[*]Either **select** *“Never remember passphrases”* (the safe, paranoid, option), or **deselect** *“Ask me before using a cached passphrases”* (the relaxed option).
[/LIST]
From then on, you can complete all of your work involving your *secret* key and your *passphrase* exclusively from the command line shell, without ever having to divert your attention to the graphical desktop environment.[/INDENT]

Run the following command, to start a session to edit your key:
```
gpg --edit-key [COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR]
```

At the *“command>”* prompt displayed by the *gpg* program, type the *“passwd”* command:
```
passwd
```

The program will prompt you for the *current* passphrase:
```
Enter passphrase:
```

Next, it will ask you to enter a *new* passphrase:
```
Enter the new passphrase for this secret key.

Enter passphrase: 
```

To ensure that you correctly typed the new passphrase, you will have to repeat it:
```
Repeat passphrase:
```

When the program redisplays its *“command>”* prompt, enter the *“save”* command, to make your changes permanent and to exit the program:
```
save
```

**_Note:_**

[INDENT]If you change your mind, and decide that you want to keep the *old* passphrase after all, then simply enter the  *“quit”* command instead, and answer the confirmation questions appropriately.[/INDENT]

[SIZE="4"][COLOR="DarkRed"]**_Appendix B: Changing the Userid of the Key._**[/COLOR][/SIZE]

If you set the userid of the key to, say, *“Local Ubuntu Intrepid Ibex Repository,”* and you subsequently transfer the key to a Jaunty Jackalope system, you will likely want to update the userid, to make it correspond to the new Ubuntu release.

Changing the userid will happen in two steps:
[LIST]
[*]Add the *new* userid;
[*]Delete the *old* userid.
[/LIST]
Just as in [COLOR="DarkRed"]***Appendix A,***[/COLOR] above, you will have to run the following command to edit your key:
```
gpg --edit-key [COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR]
```

To add the new userid to the key, type the *“adduid”* command:
```
adduid
```
The program will prompt you for the new *real name, e-mail address,* and *comment*—e.g.:
```
Real name: Local Ubuntu Jaunty Jackalope Repository
E-mail address:
Comment:
You selected this USER-ID:
    "Local Ubuntu Jaunty Jackalope Repository"

Change (N)ame, (C)omment, (E)-mail or (O)kay/(Q)uit?
```
If you then type **O** to confirm your changes, then you will have to enter your passphrase, and the program will display your key with both the old and the new userids:
```
pub  4096R/[COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR]  created: 2009-03-07  expires: 2014-03-06  usage: SC  
                     trust: unknown       validity: unknown
[ unknown] (1)  Local Ubuntu Intrepid Ibex Repository
[ unknown] (2). Local Ubuntu Jaunty Jackalope Repository
```

Next, you will have to **select** the userid that you want to delete—i.e., userid 1. To that end, type the following command:
```
uid 1
```
The program will display an asterisk (i.e., “*”) next to the selected userid:
```
pub  4096R/[COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR]  created: 2009-03-07  expires: 2014-03-06  usage: SC  
                     trust: unknown       validity: unknown
[ unknown] (1)* Local Ubuntu Intrepid Ibex Repository
[ unknown] (2). Local Ubuntu Jaunty Jackalope Repository
```

Type the *“deluid”* command to delete the selected userid:
```
deluid
```
Confirm the operation, and the selected userid will be removed:
```
pub  4096R/[COLOR="DarkRed"]**_xxxxxxxx_**[/COLOR]  created: 2009-03-07  expires: 2014-03-06  usage: SC
                     trust: unknown       validity: unknown
[ unknown] (1). Local Ubuntu Jaunty Jackalope Repository
```

Finally, enter the *“save”* command to make your changes permanent and to exit the program:
```
save
```

---

### Post by mihir786 on 2009-11-04
Hello Luvr i LAN network on my hostel and here internet connection is so slow and i keep my system up-to-date so i want to do that all students can update their ubuntu software from my repository so can u tell me in deatail what i have to do for this??

---

### Post by luvr on 2009-11-06
> **mihir786 said:**
> Hello Luvr i LAN network on my hostel and here internet connection is so slow and i keep my system up-to-date so i want to do that all students can update their ubuntu software from my repository so can u tell me in deatail what i have to do for this??

If I understand you correctly, you want to install updates (and perhaps also new software packages) to one machine from the online repositories, and store the downloaded packages into a local repository, from where the other machines can pick them up. That way, you will have to download the packages only once, instead of having each computer download them separately.

Obviously, you will have to start by setting up a local repository on your *"Master"* machine (that is, the machine on which you will download the updates and new installs). If you haven't already done so, I suggest you follow the procedure as I described it in [the first post of this thread.]("http://ubuntuforums.org/showthread.php?p=6861247#post6861247") If you know how to work with a command-line console, then I believe the procedure is explained quite clearly (but please do let me know if there's anything that confuses you about it).

Once you have the local repository correctly set up on your *"Master"* machine, it's time to allow your *"Satellite"* systems to access it as their primary source location for software updates (and, possibly, any new software that you decide to install on the *"Master"* machine).

I guess that you will want to access your local repository through your local network, right? If that is the case, then file sharing through SAMBA is by far the most convenient option. (SAMBA started life as a Free Software implementation of the Windows networking protocols, to allow Linux--and BSD and Unix--systems to share files with Windows systems; these days, however, it is getting more and more popular as a networking option among Linux systems as well.) Your *"Master"* machine will have to be set up as a SAMBA **Server,** to which your *"Satellites"* can then connect as **Clients.**

I must admit, though, that I have never set up a SAMBA server, so I cannot give you much advice about it; I believe, though, that you can easily set it up from the Ubuntu desktop. On your *"Master"* machine, just locate the folder that you want to share with the *"Satellites"* (i.e., your local repository folder), right-click on its icon, and select *"Sharing Options"*; the options that will be presented to you, should be fairly simple.

On your *"Satellite"* machines, you will have to select *"Connect to Server..."* (from the *"Places"* menu). For *Service type,* select *"Windows share"*; type in the *Server* name (i.e., the name of your *"Master"* machine) and the *Share* name (which you defined when you created the share on the server), plus, possibly the user name and password for the connection.

Once your client and server setup works, you will have to figure out how to *"mount"* the shared folder to a specific location on your client machines. I guess you should be able to define the network connection in your *"/etc/fstab"* file (or some such), but I'm afraid I won't be able to help you with this aspect at this time.

Finally, to make your *"Satellite"* machines pick up updated and new packages from your (now shared) local repository, you will have to
[LIST]
[*]Export the *"Public Key"* that you created for your local repository (see [COLOR="DarkRed"]***Step 2***[/COLOR] of the procedure as documented in the first post of this thread);
[*]Import the Public Key to all of your *"Satellite"* computers  (see [COLOR="DarkRed"]***Step 3***[/COLOR] of said procedure);
[*]Add your local repository as an APT source on all of your *"Satellite"* computers (see [COLOR="DarkRed"]***Step 9***[/COLOR] of the procedure).
[/LIST]
**_Note:_**
[INDENT]While this may all seem awfully long-winded and complex, I'm sure it's not really that hard.

In fact, I'm using a local repository myself, even though I don't share it on a network. Instead, I copy it to a USB disk (using the *"Unison"* file synchronisation tool), and from the USB disk onto each computer on which I want to use it (again using  *"Unison"*). Thus, each of these computers gets its own local copy of my local repository.

Again, please do keep in mind that I have never set up a SAMBA server, and I would have to search for more information on how to define an appropriate *"mount point"* for a shared folder on the cleint machines myself.[/INDENT]

---

### Post by k3lt01 on 2009-11-06
Hi Luvr, and mihir786, if I may make a suggestion I wouldn't use SAMBA for this. What I would do instead is set up a Repository folder (making sure to give it an appropriate name that is easily recognisable) on the "Master Machine" then enable that folder to be shared (but very importantly not written to by) with "Client Machines". I would do this by [NFS]("https://help.ubuntu.com/9.10/serverguide/C/network-file-system.html"). It is all explained in the Ubuntu Server Guide.

The client machines will then need to be pointed using NFS to the "Repository" in Software Sources. The next step would be to make sure the "Check for updates" is set to an appropriate time frame. It would be no use setting it to everyday when the Repository server is only updated once a week :lolflag:. After that you could test it by using Update Manager and clicking "Check".

---

### Post by luvr on 2009-11-07
> **k3lt01 said:**
> I would do this by [NFS]("https://help.ubuntu.com/9.10/serverguide/C/network-file-system.html").

I must say, I did think about NFS before I posted my reply, but when I wondered how the client machines would have to address the server, I realised that most local networks use DHCP. In other words, most computers will not have a fixed IP address.

In addition *(at least to the best of my knowledge)* addressing the local computers by workstation *name* won't work, because host names aren't resolved on the local network--at least, not without additional setup.

That's why I suggested SAMBA--which should make workstation names visible on the local network.

For instance, I'm running a small peer-to-peer local network, with an ADSL router as my gateway to the internet. The router, of course, has a fixed IP address on my network, but hands out *dynamic* IP addresses to my workstations; none of my workstations have *fixed* IP addresses, since I don't perform any explicit configuration on any of them. Under these conditions, SAMBA seems like the most convenient option to me. (In fact, in the past, when I was still running a Windows machine on this network, I remember playing with a Linux box as a SAMBA client that connected to the Windows machine, and that worked fine.)

Now, I have just bought a new ADSL router, which, incidentally, allows me to associate fixed IP addresses with any client machines (identified by MAC address) that I choose to define to the router; these client machines won't need any additional setup, and will continue to receive their network configuration through DHCP, but they will be assigned fixed IP addresses from the router. That should make traditional Unix networking options far more practical. In addition, if I understand the documentation correctly, the router may even provide name resolution on the local network--though, admittedly, I may have misinterpreted the docs.

Anyway, I'm not really a networking guru, so my understanding may be wrong, but that is how I believe these things work. If I'm mistaken, though, by all means, please don't hesitate to correct me; I'm always interested in learning more about the subject!

---

### Post by k3lt01 on 2009-11-07
Ah I get your thinking now, I thought SAMBA was more for Windows Networking thats why I suggested NFS. I can see your point.

---

### Post by luvr on 2010-05-13
[SIZE="4"][COLOR="DarkRed"]**_The Problem._**[/COLOR][/SIZE] 

You successfully installed the *“Adobe Flash Player Plugin”* software package (i.e., *“flashplugin-installer”*) on one computer that has full internet access, and you are making the package available locally—e.g., through a local software repository. 

You are now trying to install the package on another computer, but this time with limited or no internet access, e.g., with the following command: 
```
sudo apt-get install flashplugin-installer
``` 
When the command starts up, it produces the following output: 
```
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following extra packages will be installed: 
  ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386 nspluginwrapper 
Suggested packages: 
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs lib32asound2-plugins 
The following NEW packages will be installed 
  flashplugin-installer ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386 nspluginwrapper 
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B/34.2MB of archives. 
After this operation, 145MB of additional disk space will be used. 
Do you want to continue [Y/n]?
``` 
You notice, specifically, the line that reads ***“Need to get 0B/34.2MB of archives.”*** From this output line, you draw the conclusion that the software packages will *not* be downloaded from the internet, but that the files that you want to install, will be taken from your local repository instead. 

However, when you continue the operation, you discover that the installer still attempts to download a *“.tar.gz”* archive file; this download will, obviously, fail if the computer does not have an active internet connection—e.g.:
```
--2010-04-18 16:22:17--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2.orig.tar.gz 
Resolving archive.canonical.com... failed: Name or service not known. 
wget: unable to resolve host address `archive.canonical.com' 
download failed 
The Flash plugin is NOT installed.
```
In this post, I will explain how you can examine the *“flashplugin-installer”* package, and find a way to avoid having the package download the archive file during installation.

[SIZE="4"][COLOR="DarkRed"]**_Step 1: Getting a Copy of the *“flashplugin-installer”* Package._**[/COLOR][/SIZE]

As I mentioned in the introduction above, I’m assuming that you have already installed the *“flashplugin-installer”* package on one computer, and that you are making it available in your local software repository. You can, then, easily copy it from there to, e.g., your home directory, as follows:
```
cd
cp LocalRepository/flashplugin-installer_*.deb .
```
A copy of the *“flashplugin-installer”* package should now be present in your current working directory—as the following command will demonstrate:
```
ls -l flashplugin-installer_*.deb
```
The output from this command should look similar to the following:
```
-rw-r--r-- 1 luvr luvr 19574 2010-05-13 15:40 [COLOR="Red"]flashplugin-installer_10.0.45.2ubuntu0.9.10.1_amd64.deb
[/COLOR]
```
**_Note:_**

[INDENT]If you did install the *“flashplugin-installer”* package, but you do *not* maintain a local repository, then you should be able to copy it from the APT package cache—i.e., the *“/var/cache/apt/archives”* directory—instead:
```
cd
cp /var/cache/apt/archives/flashplugin-installer_*.deb .
```[/INDENT]
[SIZE="4"][COLOR="DarkRed"]**_Step 2: Extracting the Control Information from the Package._**[/COLOR][/SIZE]

If you want to take a look at what a software package actually *does* when you install it, you will have to extract its *control information*—which includes configuration settings and script files to guide the installation process *(as well as the **un**installation process)*.

To extract the *control information* from a Debian package file, you can use the *“dpkg-deb”* command, and pass it the *“--control”* option—the following command, for instance, will extract the *control information* from your copy of the *“flashplugin-installer”* package file:
```
dpkg-deb --control flashplugin-installer_10.0.45.2ubuntu0.9.10.1_amd64.deb

```
This command will not produce any visible output, but it will create a *“DEBIAN”* directory, in which it will copy the *control information* from the package file. You can run the following command to obtain a list of the extracted control files:
```
ls -l DEBIAN
```
The output will look something like this:
```
total 36
-rwxr-xr-x 1 luvr luvr 1548 2010-02-15 14:37 [COLOR="Green"]config[/COLOR]
-rw-r--r-- 1 luvr luvr 1941 2010-02-15 14:37 control
-rw-r--r-- 1 luvr luvr  334 2010-02-15 14:37 md5sums
-rwxr-xr-x 1 luvr luvr 5126 2010-02-15 14:37 [COLOR="Green"]postinst[/COLOR]
-rwxr-xr-x 1 luvr luvr  206 2010-02-15 14:37 [COLOR="Green"]postrm[/COLOR]
-rwxr-xr-x 1 luvr luvr 2505 2010-02-15 14:37 [COLOR="Green"]prerm[/COLOR]
-rw-r--r-- 1 luvr luvr 5438 2010-02-15 14:37 templates
```
Two of these files will be of particular interest to you, if you are trying to figure out what exactly will happen when you attempt to install the package:
[LIST][*]**config**
This is the script that will drive the *configuration* of the installation process.
In the case of the *“flashplugin-installer”* package, for example, it will decide if the supporting files will have to be downloaded, or have been made available locally.
[*]**postinst**
This is the script that will take any post-installation steps required to make the installed software fully functional.[/LIST]
These two script files can help you determine which files you will have to pre-download, and where you have to copy them, in order to keep the installer from attempting to download any further files during the installation process.

[SIZE="4"][COLOR="DarkRed"]**_Step 3: Examining the *“config”* File._**[/COLOR][/SIZE]

If you open the *“config”* file in any text editor, then you will see the following code fragment near the top of the file:
```
db_get flashplugin-installer/local
echo "423ac7830c8a55ac931acb9e07a51f2aa981aedb63b45745460b4556a10e157b  $RET/install_flash_player_10_linux.tar.gz" \
| sha256sum -c > /dev/null 2>&1 \
|| db_set flashplugin-installer/local /var/cache/flashplugin-installer
```
While these lines will likely appear confusing to you *(they surely do to me!)*—they do reveal a few potentially interesting items:
[LIST][*]**423ac7830c8a55ac931acb9e07a51f2aa981aedb63b45745460b4556a10e157b**
This strangely looking string appears to consist of a sequence of 64 hexadecimal digits.
Since it seems to get passed on to the *“sha256sum”* command, it must be a SHA-256 checksum value of some file.
[*]**install_flash_player_10_linux.tar.gz**
This string appears to be the name of a file.
Since it apparently gets passed on to the *“sha256sum”* command, together with the SHA-256 checksum value, it must be the name of the file to which the checksum applies.
[*]**/var/cache/flashplugin-installer**
This string certainly looks like some sort of a path name.
Since you have already identified a file name, it doesn’t seem all that far-fetched to assume that this is the name of the *directory* where the file should be located.

**_Note:_**

[INDENT]The path name occurs as a parameter to a *“db_set”* command *(whatever that may mean).* The *first* parameter of the command is ***“flashplugin-installer/local”***; thus, the command appears to *“set”* a data item named *“flashplugin-installer/local”* equal to the path name.

If you want to obtain a little more information on what the *“flashplugin-installer/local”* item is supposed to mean, then you may want to look for its description in the *“templates”* file (which is one of the files that make up the control information that got extracted from the package):
```
Template: flashplugin-installer/local
Type: string
Default:
Description: Location to the local file:
 Have you already downloaded the .tar.gz
 package from the Internet? If so, please enter the directory you downloaded
 it into. Do not include the filename here. If you
 have not already downloaded it, leave this blank and the package will be
 downloaded automatically.
```
This description certainly confirms your suspicions about the meanings of the file and path name strings.[/INDENT][/LIST]
**_Conclusion:_**
[INDENT]The *“config”* script looks for a file named ***“install_flash_player_10_linux.tar.gz”*** in the ***“/var/cache/flashplugin-installer”*** directory, and will calculate the checksum of the file in order to verify its integrity. If it doesn’t find the file, or if the checksum doesn’t match, then the script will force a download from the internet during the installation process.[/INDENT]
**_Note:_**
[INDENT]Newer versions of the Flash Player Plugin installer no longer look for the *“install_flash_player_10_linux.tar.gz”* file. For reference, however, I will not update this post for such newer releases. My later, similar, post on [Installing the Flash Player Plugin from a Local Mirror, without Internet Access,](http://ubuntuforums.org/showthread.php?p=9884724#post9884724) on the other hand, does work with such a newer version.[/INDENT]
[SIZE="4"][COLOR="DarkRed"]**_Step 4: Examining the *“postinst”* File._**[/COLOR][/SIZE]

Next, if you open the *“postinst”* file in any text editor, then you will find the following code near the top of the file:
```
FLASH_VERSION=10.0.45.2
FILENAME=adobe-flashplugin_${FLASH_VERSION}.orig.tar.gz
SHA256SUM_TGZ="30be012f0a680ef54fd6bca50c6bdb4addf29368b3d105496daf480abd8ac97b"
PARTNER_URL=http://archive.canonical.com/pool/partner/a/adobe-flashplugin/$FILENAME
```
These statements apparently refer to a file named ***“adobe-flashplugin_10.0.45.2.orig.tar.gz”***; they specify the expected SHA-256 checksum of the file, and the location from which it should be downloaded.

[SIZE="4"][COLOR="DarkRed"]**_Step 5: Building the *“SHA256”* File._**[/COLOR][/SIZE]

It should be clear by now, that you will have to pre-download two files:
[LIST][*]install_flash_player_10_linux.tar.gz
[*]adobe-flashplugin_10.0.45.2.orig.tar.gz[/LIST]
Also, the installer will verify their checksums, and it will consider them valid only if the checksums are correct. After you download the files, it may, therefore, be a good idea to *manually* verify their checksums before actually installing the package—to ensure that the files were downloaded without error.

You may, therefore, want to create a *checksum verification file* first—i.e., a text file that lists each file that you want to verify, together with its expected checksum value. Each line of the verification file should have the following format:
[LIST][*]The *checksum value*—which should be a 64-character string of hexadecimal digits;
[*]A single blank space;
[*]A single asterisk (i.e., **“*”**);
[*]The name of the file.[/LIST]
To determine the actual contents of the *checksum verification file,* you should refer back to the *“config”* and *“postinst”* scripts discussed above. The result should look like this:
```
423ac7830c8a55ac931acb9e07a51f2aa981aedb63b45745460b4556a10e157b *install_flash_player_10_linux.tar.gz
30be012f0a680ef54fd6bca50c6bdb4addf29368b3d105496daf480abd8ac97b *adobe-flashplugin_10.0.45.2.orig.tar.gz
```
Save this text under any appropriate name—e.g., *“SHA256.”*

[SIZE="4"][COLOR="DarkRed"]**_Step 6: Downloading the *“install_flash_player_10_linux.tar.gz”* File._**[/COLOR][/SIZE]

To download the *“install_flash_player_10_linux.tar.gz”* file, you will have to use your browser to navigate to the following URL:
```
http://get.adobe.com/flashplayer
```
For the *“version to download,”* select ***“.tar.gz for Linux,”*** and then click *“Agree and install now.”* You should save the file to the same directory where you created the *“SHA256”* file, above.

[SIZE="4"][COLOR="DarkRed"]**_Step 7: Downloading the *“adobe-flashplugin_10.0.45.2.orig.tar.gz”* File._**[/COLOR][/SIZE]

To download the *“adobe-flashplugin_10.0.45.2.orig.tar.gz”* file, you can use the *“wget”* utility. The location from which to download the file, is given by the *“PARTNER_URL”* value in the *“postinst”* script, as documented above. Run the following command to get the file, and save it into your current working directory:
```
wget http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2.orig.tar.gz
```

[SIZE="4"][COLOR="DarkRed"]**_Step 8: Verifying the Downloaded Files._**[/COLOR][/SIZE]

You should make sure that your current working directory now contains the following three files:
[LIST][*]SHA256
[*]install_flash_player_10_linux.tar.gz
[*]adobe-flashplugin_10.0.45.2.orig.tar.gz[/LIST]
To verify the integrity of the downloaded files, you can now run the following command:
```
sha256sum -c SHA256
```
The output from this command should tell you that the files are OK:
```
install_flash_player_10_linux.tar.gz: OK
adobe-flashplugin_10.0.45.2.orig.tar.gz: OK
```

[SIZE="4"][COLOR="DarkRed"]**_Step 9: Installing the Flash Player Plugin, Using the Downloaded Files._**[/COLOR][/SIZE]

From now on, whenever you want to install the Flash Player plugin on another computer, you can first copy the two downloaded files into its *“/var/cache/flashplugin-installer”* directory, as follows:
```
sudo mkdir /var/cache/flashplugin-installer
sudo cp install_flash_player_10_linux.tar.gz /var/cache/flashplugin-installer
sudo cp adobe-flashplugin_10.0.45.2.orig.tar.gz /var/cache/flashplugin-installer
```
If you subsequently install the *“flashplugin-installer”* package on the computer, then the local copies of these files will be used, so the installer won’t have to download them again.

**_Important:_**

[INDENT]The required versions of the downloaded files depend both on the Ubuntu release, and on the current Flash Player version. You will have to download new versions of the files (as identified in the *“config”* and *“postinst”* scripts documented above) when you need to install them under a different Ubuntu release, or when the Flash Player gets updated.[/INDENT]

---

### Post by sineau on 2010-10-13
Hi luvr,
I used your HowTo, and it actually solved my problem (like having to burn CD with APTonCD). So first of all thanks a lot. But there's is still one problem which i can't figure it out by myself. 
When I load my repository in Synaptic, it doesn't show all packages I stored locally which are available in "Packages" file. Where this problem may come from? I know they're there, and I redid the tutorial twice. Also there are no older versions of packages.

---

### Post by luvr on 2010-10-15
> **sineau said:**
> When I load my repository in Synaptic, it doesn't show all packages I stored locally which are available in "Packages" file. Where this problem may come from?
Without any further information, the only reason I can think of would be the *package architecture* that they apply to. For instance, you may be running a 32-bit (*"i386"*) system, while the packages are targeted at the 64-bit ("*amd64"*) architecture (or vice versa).

Could that be the case here?

---

### Post by poram on 2010-10-25
Have followed the howto provided at the beginning of  the thread to add a Release file to my local repository of inhouse packages, however when I try to install the package, I am getting:

WARNING: The following packages cannot be authenticated!
  <package-name>

How can I overcome this issue as we want to automate the process and this will stop it from installing automatically.

The local repository has been added to the target system's sources.list file.

---

### Post by luvr on 2010-10-25
> **poram said:**
> WARNING: The following packages cannot be authenticated!
  <package-name>
There's only one reason I can think of why you would get this error: Your public key wasn't added to the APT list of trusted keys.

Specifically, you should review **Step 3,** *"Importing your Public Key into the APT List of Trusted Keys"* in the original post. As documented there, you can run the following command to verify if your key was successfully imported into APT:
```
sudo apt-key list
```

---

### Post by poram on 2010-10-26
> **luvr said:**
> There's only one reason I can think of why you would get this error: Your public key wasn't added to the APT list of trusted keys.

Specifically, you should review **Step 3,** *"Importing your Public Key into the APT List of Trusted Keys"* in the original post. As documented there, you can run the following command to verify if your key was successfully imported into APT:


The key was successfully imported on both the target server and also the local repository's server.

---

### Post by luvr on 2010-10-27
> **poram said:**
> The key was successfully imported on both the target server and also the local repository's server.
Do you get the error on the local repository server, or on the target server, or both?

---

### Post by poram on 2010-10-28
> **luvr said:**
> Do you get the error on the local repository server, or on the target server, or both?

On the target server when we attempt to install the package.

---

### Post by luvr on 2010-10-28
> **poram said:**
> On the target server when we attempt to install the package.
Could you, then, try and manually verify the digital signature on the *Release* file? To this end, do the following (on your target machine):
[LIST][*]Open a command-line shell window, and go to the directory where you keep your local repository.[/LIST]
[LIST][*]The directory should contain a *“Release”* and a *“Release.gpg”* file—as you can verify with the following command:
```
ls -l Release*
```
[*]Now type the following command, to manually verify the signature:
```
gpgv --keyring /etc/apt/trusted.gpg Release.gpg Release
```[/LIST]
Please post the output from this command.

---

### Post by poram on 2010-10-28
> **luvr said:**
> Could you, then, try and manually verify the digital signature on the *Release* file? 

[LIST]
[*]type the following command, to manually verify the signature:
```
gpgv --keyring /etc/apt/trusted.gpg Release.gpg Release
```
[/LIST]
 
# gpgv --keyring /etc/apt/trusted.gpg Release.gpg Release
gpgv: Signature made Mon 25 Oct 2010 17:55:14 EST using RSA key ID A73368E9
gpgv: Good signature from "Systems (SNG) <headoffice-systems@xxxx.xx.xx>"

---

### Post by luvr on 2010-10-30
> **poram said:**
> # gpgv --keyring /etc/apt/trusted.gpg Release.gpg Release
gpgv: Signature made Mon 25 Oct 2010 17:55:14 EST using RSA key ID A73368E9
gpgv: Good signature from "Systems (SNG) <headoffice-systems@xxxx.xx.xx>"

Hmmm... This definitely confirms that your key is correctly installed, and that the digital signature on your *Release* file is correct.

I'm a bit at a loss now. I haven't used a local repository since I upgraded to Lucid, so I wanted to set up a new one to see if I could reproduce your problem. However, I had a disk crash on one of my computers earlier today, so I will have to reinstall first.

In the mean time, I have a few more questions to ask:
[LIST][*]Could you tell me if your problem occurs on your local repository server, too, if you attempt to install the package there?
[*]How does your target machine get access to your local repository? Do you share it over your network (and if so, through which means)? Or do you copy your repository over to a local disk on the target machine (or to an external disk that you connect to the target machine)?
[*]Which package are you trying to install? Is the package available from the Ubuntu repositories as well, or did you get it anywhere else?[/LIST]

By the way, if you want to automatically force installation of packages that cannot be authenticated, then you can use the *“--allow-unauthenticated”* option when you run *apt-get*—e.g.:
```
sudo apt-get --allow-unauthenticated install *packagename*
```
I’m not a fan of this option, since it defeats the purpose of a trusted repository in the first place, but it may occasionally be helpful.

---

### Post by luvr on 2010-10-31
> **poram said:**
> WARNING: The following packages cannot be authenticated!
  <package-name>

Honestly, I have no idea how this is happening. I have just set up a local repository for the [LibreOffice]("http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta2/deb") packages, and I simply cannot reproduce the problem.

I set up the repository on a local disk on one machine, then copied it to an external disk, hooked the disk up to another machine, copied the repository directory on to a local disk on that machine, imported the appropriate public key into the APT system (*&#8220;sudo apt-key add pubkeyfile&#8221;*), added the repository to the *&#8220;sources.list&#8221;* file, reloaded the package information (*&#8220;sudo apt-get update&#8221;*)&#8212;and I could subsequently install any of the LibreOffice packages without further ado.

I'm probably asking a silly question now, but you couldn't by any chance have ***multiple*** signing keys available on your repository server, could you? To verify, you can run the following command:
```
gpg --list-keys
```
This should list just one entry; in my case, for example, it produces the following output:
```
/home/luvr/.gnupg/pubring.gpg
-----------------------------
pub   4096R/[COLOR="DarkRed"]**18925208**[/COLOR] 2010-10-31
uid                  Local Ubuntu Lucid Lynx Repository
```

**ADDENDUM:** Before you go any further, perhaps it would be a good idea to verify if the checksums of the package lists (i.e., *&#8220;Packages&#8221;* and *&#8220;Packages.gz&#8221;*), and of the packages themselves, are correct. In the following, I will be using the GNU version of the *awk* utility to make the checks&#8212;which, depending on your Ubuntu release, you may have to install first, like this:
```
sudo apt-get install gawk
```
Then, go to the directory that holds your local repository, and run the following two commands:
```
gawk --posix '/^ [[:xdigit:]]{32} / { print $1 " *" $3 ; }' Release | md5sum -c
gawk --posix '/^Filename: / { filename = $2 } /^MD5sum: / { print $2 " *" filename }' Packages | md5sum -c
```
If all goes well, the first command will tell you that the *&#8220;Packages&#8221;* and *&#8220;Packages.gz&#8221;* file are **&#8220;OK&#8221;**; the second command should tell you that all of your packages are **&#8220;OK&#8221;** as well.

You have already verified the digital signature on your *&#8220;Release&#8221;* file at an earlier occasion; in addition, if all checksums turn out to be OK, then the *contents* of your local repository is correct, and there must be some (as of yet unidentified) problem with the APT system itself, if it complains about packages that cannot be verified.

---

### Post by MLA Style Research Paper on 2012-04-17
Mate, your images are superb however , you unquestionably will need a lot more articles. Look at out a few of the [How To Write An Essay]("http://www.royalessays.com/how_to_write_an_essay") freelance internet writers on elance or freelancer.com there are some bargains.

---

