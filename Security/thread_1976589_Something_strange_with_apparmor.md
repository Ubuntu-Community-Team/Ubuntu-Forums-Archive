---
title: "Something strange with apparmor"
date: 2012-05-09
forum: Security
---

### Post by desire.linux on 2012-05-09
Either it's me doing something seriously wrong, or something is seriously wrong with apparmor!

I've confined a program with apparmor to restrict its write access to the file system.

But everywhere the confined program has read access _only_, it can also delete any file and folder trough its file browser if the owner of the program also owns the files and folders in question. I thought it had to have write access in the profile to do that. How do I stop the application from deleting files and folders with apparmor?

The profile does work somehow, because the program can't manipulate or write to files and folders where it only has read access. But it can delete all of them without any problem.

Please help me out here! :-/

---

### Post by desire.linux on 2012-05-09
I got help from a security guru to look at my apparmor problem, and his concision is simple: **apparmor is broken!**

It works only partially on some applications, and should not be trusted AT ALL to secure a system!

We tested the image viewer Gwenview that's strictly confined with apparmor. All executables in the profile are inherited, so they should follow the apparmor profile for Gwenview. Hence Gwenview can't start external none confined programs to mess around on the filesystem.

Gwenview, being strictly confined with apparmor, can create files and folders, and delete files and folders, at the areas of the file system where it does not have write access, only read access. This happens when the owner of the folders and files is the same as the owner who runs Gwenview. Hence apparmor simply skips its own access control for such actions and jumps directly to traditional DAC. It simply doesn't work!

Though it does manage to deny modifications of existing files, like overwrite, so it works partially. And it seems to stop execution unless you allow it to. But with such a major security hole in the apparmor framework in the first place, it's impossible to know where it might brake at other places.

This is probably a huge security hole in the framework that hopefully will be fixed soon for those who still trust and rely on apparmor.

My friend told me that this is one of the reaons why apparmor isn't very popular among other Linux distros and was rejected by Debian. It's utterly bad and flawed, and he urges me to use tomoyo or selinux instead. Apparmor is a great idea, because it's so simple and user friendly, but unfortunately an idea is all it is.

So now you're warned! And end of story.

For those who are interested, Fedora uses selinux by default and it has a GUI to make things simpler. I know that Ubuntu wants to keep things simple, but on the cost of our security? I'll rather use more time and patience on a more complex system, like Fedora, and obviously stay a lot safer.

---

### Post by CharlesA on 2012-05-09
It isn't a problem with apparmor, it is the way Linux file permissions work. The owner of a file can delete files even if they do not have write access to them.

---

### Post by bodhi.zazen on 2012-05-09
Actually these permissions are determined by the permissions on the DIRECTORY not the file.

```
# **_Notice how the directory test is "ro"_**
bodhi@ufbt:~/Documents$ ls -l | grep test
**[COLOR="DarkGreen"]dr-xr-x[/COLOR]**--- 2 bodhi bodhi 4096 2012-05-09 15:29 test

bodhi@ufbt:~/Documents$ ls -l test
**[COLOR="DarkGreen"]-rw-rw-r--[/COLOR]** 1 bodhi bodhi 0 2012-05-09 15:29 file

# But I can read and write to the file "file"
bodhi@ufbt:~/Documents$ echo "can write" >> test/file
bodhi@ufbt:~/Documents$ cat test/file
**[COLOR="DarkGreen"]can write[/COLOR]**

# But I can not delete it
bodhi@ufbt:~/Documents$ rm test/file
rm: remove regular file `test/file'? y
[COLOR="DarkRed"]**rm: cannot remove `test/file': Permission denied**[/COLOR]
```

See [http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

> Read permission. On a regular file, the read permission bit means the file can be opened and read. On a directory, the read permission means you can list the contents of the directory.

Write permission. **On a regular file, this means you can modify the file, aka write new data to the file.** **[COLOR="DarkRed"]In the case of a directory, the write permission means you can add, remove, and rename files in the directory. This means that if a file has the write permission bit, you are allowed to modify the file's contents, but you're allowed to rename or delete the file only if the permissions of the file's directory allow you to do so.[/COLOR]**

Execute permission. In the case of a regular file, this means you can execute the file as a program or a shell script. On a directory, the execute permission (also called the "search bit") allows you to access files in the directory and enter it, with the cd command, for example. However, note that although the execute bit lets you enter the directory, you're not allowed to list its contents, unless you also have the read permissions to that directory.

---

### Post by bodhi.zazen on 2012-05-09
> **desire.linux said:**
> I got help from a security guru to look at my apparmor problem, and his concision is simple: **apparmor is broken!**

Sounds as if your security guru does not understand Linux permissions.

In addition, if you need help with apparmor, you will need to post your apparmor profile for the program you are trying to confine. I can not tell from your original post if you are using one or two applications. You do understand each application needs it's own profile.

---

### Post by Hungry Man on 2012-05-09
I get that this isn't a flaw or that dangerous, after all deleting a file it owns isn't a biggie, but how would one stop it from doing this? I would have thought denying write access would do this.

---

### Post by OpSecShellshock on 2012-05-09
> **Hungry Man said:**
> I get that this isn't a flaw or that dangerous, after all deleting a file it owns isn't a biggie, but how would one stop it from doing this? I would have thought denying write access would do this.

I think you'd stop it by denying write access to the directory. Think of the files as the contents of the directory in the way that words are the contents of a file (kind of). You would need to deny write permissions to the directory to prevent addition/deletion of files, and also deny write access to the file in order to prevent modification of it.

---

### Post by bodhi.zazen on 2012-05-09
> **Hungry Man said:**
> I get that this isn't a flaw or that dangerous, after all deleting a file it owns isn't a biggie, but how would one stop it from doing this? I would have thought denying write access would do this.

It is not a flaw or dangerous, it is users not understanding permissions and/or apparmor.

You would stop it by learning permissions and/or apparmor and configuring them properly.

I think you should re-read my first post, I demonstrated how to configure rw access to a file, without permission to delete the file, with permissions.

With apparmor you would use a rather then w

---

### Post by Hungry Man on 2012-05-09
I'm not saying it's a flaw or dangerous. If a program creates the file it can then delete it, yes? That's the perceived issue, right?

And thanks I'll read it.

---

### Post by bodhi.zazen on 2012-05-09
> **Hungry Man said:**
> I'm not saying it's a flaw or dangerous. If a program creates the file it can then delete it, yes? That's the perceived issue, right?

And thanks I'll read it.

I am not really sure what you are asking here. Are you asking about permissions ? Apparmor ? deleting files ? which files ?

Permissions are your first line of defense, period. If standard (DAC) permissions deny access, apparmor policy is never consulted.

> AppArmor provides an additional permission check to DAC. **[SIZE="2"]DAC is always checked first such that if it does not allow access, the AppArmor permission checks will not be performed.[/SIZE]**

[http://wiki.apparmor.net/index.php/QuickProfileLanguage#How_AppArmor_file_permissions_differ_from_DAC](http://wiki.apparmor.net/index.php/QuickProfileLanguage#How_AppArmor_file_permissions_differ_from_DAC)

Apparmor file permissions are covered in the man page:

[http://manpages.ubuntu.com/manpages/precise/man5/apparmor.d.5.html](http://manpages.ubuntu.com/manpages/precise/man5/apparmor.d.5.html)

> Access Modes Details
       r - Read mode
           Allows the program to have read access to the file or directory
           listing. Read access is required for shell scripts and other
           interpreted content.

       w - Write mode
           Allows the program to have write access to the file. Files and
           directories must have this permission if they are to be unlinked
           (removed.)  Write mode is not required on a directory to rename or
           create files within the directory.

           This mode conflicts with append mode.

       a - Append mode
           Allows the program to have a limited appending only write access to
           the file.  Append mode will prevent an application from opening the
           file for write unless it passes the O_APPEND parameter flag on
           open.

           The mode conflicts with Write mode.

With those references as background, the answer to the OP question is to use (DAC) permissions to configure permissions on directories and files appropriately, as I demonstrated in my post. With proper DAC permissions, permission is denied and the apparmor profile never comes into play.

---

### Post by desire.linux on 2012-05-09
> **bodhi.zazen said:**
> Sounds as if your security guru does not understand Linux permissions.

Maybe so, but please make sure that we have understood you right on this one:

If I confine a program (a program with file browsing and editing capabilities) with apparmor, and make sure that this program is confined with no write permissions to the file system at all, only read access (like /** r,), apparmor will still allow this program to delete files and folders if they are owned by the same user who runs the confined program? Even create new folders?

> **wiki.apparmor.net/index.php/AppArmor_Core_Policy_Reference]
w - write - permission to create, delete, write to a file and extend it 
[/QUOTE]I've interpreted the apparmor wiki as you'll need the write flag to be able to e.g. delete files and create new folders.

I've also interpreted apparmor as an application firewall that should stop write access even if the owner of the confined program owns the directories being written too. Apparmor should have been that _extra layer of security_!

[QUOTE=bodhi.zazen said:**
>  In addition, if you need help with apparmor, you will need to post your apparmor profile for the program you are trying to confine. I can not tell from your original post if you are using one or two applications. You do understand each application needs it's own profile.

I don't have access to the profile from this computer.

It was the Gwenview image viewer that was tested. I don't know how it works. Maybe it mysteriously calls another program somehow for folder editing. Aa-genproof didn't notice that anyway.

My friend is pretty sure there's something wrong with apparmor. If apparmor can't confine a program from deleting and writing to the user's own home folder, then I'm having trouble seeing the benefits of using apparmor at all.

---

### Post by bodhi.zazen on 2012-05-09
> **desire.linux said:**
> Maybe so, but please make sure that we have understood you right on this one:

If I confine a program (a program with file browsing and editing capabilities) with apparmor, and make sure that this program is confined with no write permissions to the file system at all, only read access (like /** r,), apparmor will still allow this program to delete files and folders if they are owned by the same user who runs the confined program? Even create new folders?

I've interpreted the apparmor wiki as you'll need the write flag to be able to e.g. delete files and create new folders.

I've also interpreted apparmor as an application firewall that should stop write access even if the owner of the confined program owns the directories being written too. Apparmor should have been that _extra layer of security_!



I don't have access to the profile from this computer.

It was the Gwenview image viewer that was tested. I don't know how it works. Maybe it mysteriously calls another program somehow for folder editing. Aa-genproof didn't notice that anyway.

My friend is pretty sure there's something wrong with apparmor. If apparmor can't confine a program from deleting and writing to the user's own home folder, then I'm having trouble seeing the benefits of using apparmor at all.

Hard to say from what little you have posted.

You need to post the apparmor profile and describe what you are trying to have apparmor do exactly.

As far as > I'm having trouble seeing the benefits of using apparmor at all.

Well, if you can't describe what you want apparmor to do for you, and can not post a profile, I guess it is hard to see the benefits.

Example:

I want to use apparmor to restrict access of some programs in my home directory.

Specifically, I do not want firefox to have any access to ~/.ssh

Here is what I use:

```
  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/* r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/{Desktop,Downloads}/ r,
  owner @{HOME}/{Desktop,Downloads}/** rw,

  # per-user firefox configuration
  owner @{HOME}/.mozilla/ rw,
  owner @{HOME}/.mozilla/** rw,
  owner @{HOME}/.mozilla/**/*.sqlite* k,
  owner @{HOME}/.mozilla/**/.parentlock k,
  owner @{HOME}/.mozilla/plugins/** rm,
  owner @{HOME}/.mozilla/**/plugins/** rm,

  #
  # Extensions
  # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
  # Allow 'x' for downloaded extensions, but inherit policy for safety
  owner @{HOME}/.mozilla/**/extensions/** mixr,

  # Flash
  owner @{HOME}/.adobe/ rw,
  owner @{HOME}/.adobe/** rw,
  owner @{HOME}/.macromedia/ rw,
  owner @{HOME}/.macromedia/** rw,

  # Allow flash to use video acceleration
  /dev/nvidiactl rw, 
  /dev/nvidia0 rw,

  # Other permissions in HOME directories
  owner @{HOME}/.config/ r,
  owner @{HOME}/.config/** r,
  owner @{HOME}/.config/ibus/bus/ rw,
```

So you need to start with a definition of a purpose ;)

---

### Post by rookcifer on 2012-05-09
> **desire.linux said:**
> Maybe so, but please make sure that we have understood you right on this one:

If I confine a program (a program with file browsing and editing capabilities) with apparmor, and make sure that this program is confined with no write permissions to the file system at all, only read access (like /** r,), apparmor will still allow this program to delete files and folders if they are owned by the same user who runs the confined program? Even create new folders?

As Bohdi said, we would need to see the profile.  One of three things are happening here, in my opinion:

1) You are not understanding the syntax in the profile.

2) You are allowing the profile to call some other executable as unconfined (Ux).  

3) The profile abstractions are allowing the profile to do things you might not want.

Also from the AppArmor Wiki:
> 
AppArmor leverages DACs existing labeling (but not permissions) for owner and groups, and does not have a concept of user or owner that is separate from the systems user or owner. Certain security models require that policy be setup in conjunction with other linux security controls, such as owner and groups and the pam_cap module. 

Also, AppArmor has an IRC channel you can visit if you want to talk to the real experts (developers).  It's on OFTC, channel: #apparmor.

---

### Post by desire.linux on 2012-05-11
Here's a mail from my security guru friend about the issue:

> 
This has less to do with DAC and more to do with apparmor not appreciating socket files that certain applications are programmed to use to pipe/access other programs. This makes apparmor primitive, highly limited and outrageous dangerous to inexperienced users who rely on it as an application firewall. Not to mention it actually doesn't support all applications, I mean applications that use socket files.

An application confined with apparmor may call another application to do certain stuff, like an execute. An image viewer may call a file manager to be able to manipulate files and folders. Normally you would give the main application and its apparmor profile execute right to that external application by inheriting the current profile, so that the external application is just as much confined as the primary application. But some programs call other programs trough socket files just by reading and writing to them. And if you give apparmor read and write access to a certain socket file, needed for the main application to work properly, that application is free to call any other program or application it likes to do whatever it wants, without being confined nor inherited by the main profile. And apparmor doesn't understand that by writing to a socket file, it pipes actions that normally would be denied by the main profile to applications that are not confined. Hence your problem.

This is where selinux doesn't fail. The bad thing about selinux is that you'll need to be a skilled programmer to make any sense and use of it.

Just make sure that you do severe investigations when you let an apparmor profile read and write to files that look like this: [COLOR=Red]s[/COLOR]rw-rw-rw-. The best is to avoid those programs altogether if you need to confine them with apparmor.
I don't know, but maybe this makes things more clear. Gwenview does need read and write access to a socket file within /tmp to be able to manage files and folders. I've just not figured out which program is uses and when. :(

---

### Post by bodhi.zazen on 2012-05-11
Sounds more like an opinion then fact. You are running in circles as you have not stated what it is you are wanting to do, what restrictions you want to place on an application, nor have you posted an apparmor profile.

It is certainly possible you have found a bug. It could be apparmor does not do what you think or want it to do. It could be a faulty profile. None of those possibilities makes apparmor "highly limited".

In fact, statements such as "This makes apparmor primitive, highly limited and outrageous dangerous to inexperienced users" amount to nothing more then FUD, play no role in support, education, or security, and is unprofessional.

It suggests your security expert is giving you an opinion rather then quality advice, does not appreciate apparmor, or that you may be using the wrong tool for the task. It may well be that selinux is a better option.

If you would like support for apparmor, please provide the necessary information.

If you wish to learn to use apparmor, start with 

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

selinux is here : [http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/)

Yes there is a learning curve to both tools. Yes both tools have advantages and disadvantages.

---

