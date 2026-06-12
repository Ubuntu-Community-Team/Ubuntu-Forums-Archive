---
title: "Using DDEV in WSL without being Windows admin"
date: 2023-09-28
forum: Virtualisation
---

### Post by francescopesce on 2023-09-28
[COLOR=#000000][FONT=&amp]Hi,[/FONT][/COLOR][COLOR=#000000][FONT=&amp]We have a Win 11 PC used by a developer (Jhon) and administered by an IT admin (Frank).[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]On this PC we have WSL, on which runs Ubuntu (administered directly by Jhon), on which runs DDEV.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]When Jhon creates a new DDEV project, DDEV tries to run GSUDO, for which the Windows admin password (Frank's password) is requested.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]How does Frank get Jhon to do his work without being called to insert the password for every new project and without making jhon a Win 11 admin?[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Is it possible to state that GSUDO may be run without Windows admin password?[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Thank you![/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-09-28
Is the User (Jhon) added to the docker group to be able to do Docker as a Non-Admin User?

Which version of DDEV?

Because, I thought (and I might be wrong with that), but isn't DDEV (itself, after version 1.6.0) supposed to error on being ran as root?
RE: 
[https://github.com/ddev/ddev/issues/1379](https://github.com/ddev/ddev/issues/1379)
[https://ddev.readthedocs.io/en/latest/users/project/](https://ddev.readthedocs.io/en/latest/users/project/)

Seems to me as being a permissions and group membership problem. I understand that there are caveats you have to do in the commands to be able to run DDEV in WSL2 because of the different underlying file structure and networking, but that is what that seems to me.

Hint: In both Windows and Linux, as an Administrator, I gave Security Groups just enough access and permissions they needed to do what their job entailed. I then set Users as a member of that Group. 

I didn't want to be called every time someone couldn't do what there job needed on a daily basis. No-one is non-expendable. Real-life happens. So I set up those kinds of things to continue on in the future. Change a User for that: Add the new user to the Group. Remove the User that is no longer there.

Your Admin can check the group membership, inherited permissions and ACL access for groups and Users. And test them for a specific user.

Note: WSL2 is a Linux compatibility layer, so there are things that are different. Such as, for example, some of the basic Linux utilities are not actually there.

---

