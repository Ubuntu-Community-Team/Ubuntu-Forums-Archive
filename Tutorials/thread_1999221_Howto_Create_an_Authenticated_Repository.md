---
title: "Howto: Create an Authenticated Repository"
date: 2012-06-07
forum: Tutorials
---

### Post by ColinMcQueen on 2012-06-07
This is my first tutorial and I decided to write one because I had a hard time finding documentation on how to create an authenticated repository. After struggling to trying to create my first repository, I felt I should share this knowledge so anyone like me doing this the first time can have a reference point.

**Requirements:**
[LIST]
[*]Packages: apt-utils (Should be installed by default), dpkg-dev, a web server (apache2), and dpkg-sig (In Ubuntu Universe Repository)
[*]Base Directory for repository
[*].deb files
[/LIST]

**Installing the Required Packages**
[LIST=1]
[*]Type the following commands:
```
sudo apt-get install dpkg-dev
sudo apt-get install apache2
sudo apt-get install dpkg-sig
```
[/LIST]

**Create the Repository Directory Structure**
Note: If you do not create the repository in the /var/www directory then you will have to create a symbolic link inside that directory linking to your repository directory

For example (Assume I am in home directory):
```
sudo ln -s ~/repository_dir /var/www/repository_dir
```

[LIST=1]
[*]I am creating my repository in the /var/www directory using this command

(I am in the /var/www directory when executing these commands)
```
sudo mkdir -p repository_dir/dists/stable/main/binary
```

[*]Import the deb files to the binary directory

(I am in the binary directory when executing these commands)
```
sudo mv location_of_file/file1.deb .
sudo mv location_of_file/file2.deb .
```
[/LIST]

**Authenticating Repository and Packages**
[LIST=1]
[*]Create a GPG key pair using the following command

```
gpg --gen-key
```

[*]Since we are only using our key for only generating digital signatures use RSA because it is more powerful and make the key 4096 bits for maximum security (The higher the keysize the more computer resources)

```
Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection? 4
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 4096
Requested keysize is 4096 bits
```

[*]I chose "key does not expire" for how long it should be valid

```
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y
```

[*]I only included the name for the User ID, you can include email and a comment

```
You need a user ID to identify your key; the software constructs the user ID from the Real Name, Comment and Email Address in this form:
    "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"

Real name: Repository
Email address:
Comment:
You selected this USER-ID:
    "Repository"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
```

[*]You need a paraphrase to protect your secret key, choose one you will remember
[*]Follow what the output suggests to gain more entropy :p
[*]You should get output similar to this

```
gpg: key 041DA354 marked as ultimately trusted
public and secret key created and signed.

gpg: checking the trustdb
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
pub   4096R/041DA354 2012-06-01
      Key fingerprint = 2253 4C89 DE74 CF68 39D7  2A2E DB3E 384F 041D A354
uid                  Repository
```

[*]You can list your keys anytime using the following

```
gpg --list-keys
```

[*]Export your public key that was generated to a text file and store it in the root of the repository

```
sudo gpg --output keyFile --armor --export 041DA354
```

[*]Sign the packages with your key

```
sudo dpkg-sig --sign builder file1.deb
sudo dpkg-sig --sign builder file2.deb
```

[*]On another computer to access and install these packages, edit the /etc/apt/sources.list file to update the package list for your repository

(You can use a text editor, I used vi)
```
sudo vi /etc/apt/sources.list
```

Add this to the list, this can be different like the Ubuntu repositories depending on how you set yours up
```
deb http://10.31.31.89/repository_dir/dists/stable/main/binary /
```

Note: After editing the sources.list, update the package list to include our repository, it is okay if you receive an error if it cannot find packages for our repository, we did not create the index file yet

[*]Get the public key from the repository on the computer trying to access the packages from the repository

```
wget -O - http://10.31.31.89/repository_dir/keyFile | sudo apt-key add -
```

[*]To view the added key use the following

```
apt-key list
```

[*]Back on the computer with the repository, you will need to change the ownership of the directory structure including everything in it to use your user, unless you want it to be set as root

(In my repository_dir directory)
```
sudo chown user:user -R .
```

[*]Create an index file for the repository called Packages in the same directory as the deb files and zip it, you need to keep the uncompressed Packages file in there too

(In my binary directory)
```
apt-ftparchive packages . > Packages
gzip -c Packages > Packages.gz
```

[*]Create a Release, InRelease, and Release.gpg file

(Still in my binary directory)
```
apt-ftparchive release . > Release
gpg --clearsign -o InRelease Release
gpg -abs -o Release.gpg Release
```

[*]Update the package list for the computer you want to install the packages too and install the package

```
sudo apt-get update
sudo apt-get install file1
```
[/LIST]

I learned a lot about repositories and packages while doing this task for work and I hope this helps some people out. I suggest for users doing this to read up on repositories on Debian's site to learn more about repositories. I read that to understand the structure of a repository.

---

