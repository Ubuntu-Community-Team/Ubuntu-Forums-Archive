---
title: "Create RPM with binaries"
date: 2010-10-25
forum: Ubuntu Dev Link Forum
---

### Post by pelotoescogorciao on 2010-10-25
Hi,

I've developed a program in Ubuntu and now I want to create a RPM with the binaries to deploy it in SUSE and Fedora. 

My binaries are located here:

/home/me/myProject/myProjectApp
/home/me/myProject/readme.txt

And I want to create a RPM that could place them into:
/opt/myProject/myProjectApp
/opt/myProject/readme.txt

Nothing complicated as you see.

I've created this .spec file:

```

Name:       myProject
#Icon:        ./myProject.png
Summary:   A project I did
Version:   0.4.4
Release:   1
License:   Proprietary
Vendor:    Me
URL:        http://www.someURL.com
Group:     Graphics
Requires:  %{_lib}qt4>=4.6.3 %{_lib}uuid1 >= 2.17.2
Packager: Me
BuildArch: i586
BuildRoot: /home/me/myProject/



%description
A project
 
%prep
%setup -q

%install

%clean
rm -rf /opt/myProject

%files
%defattr(-,root,root)

%dir /opt/myProject
/home/me/myProject/myProjectApp
/home/me/myProject/readme.txt

%changelog
* Tue Oct 26 2010 - Me
- Initial implementation


```and, to create the RPM I do this:

rpmbuild -bb mySpecFile.spec

but this error occurs:
"There is no 'Source:' in the spec file"

which is dumb, because I specified the "-bb" param to indicate rpmbuild that I want to make a RPM using the precompiled binaries...

I also I'm not sure how to indicate the files in the %files section, even when I searched for a lot of examples in the Internet.
How can I copy my file located at /home/me/myProject/readme.txt to the installation's folder /opt/myProject/readme.txt properly, pls?
In Windows's NSIS The "File" must be used as "File /home/me/myProject/readme.txt /opt/myProject/readme.txt" which is pretty intuitive... but with RPM all is very complicated...

Please, any help indicating what I'm making wrong will be very appreciated.
Thanks.

ps: Is there any intuitive and easy-to-use GRAPHICAL tool to make RPMs, pls? Something like Debreate for making .deb files...

---

