---
title: "Packages not installing"
date: 2006-09-15
forum: Repositories &amp; Backports
---

### Post by Waqas Ahsan on 2006-09-15
hi
i am running Ubuntu Dapper. i need to install "plplot-tcl-dev" so i run the command:

> sudo apt-get install plplot-tcl-dev

the result is :
> 
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  plplot-tcl-dev: Depends: libplplot9 (= 5.3.1-8ubuntu1) but it is not going to be installed
                  Depends: plplot-tcl but it is not going to be installed
E: Broken packages

i have also tried using the packet manager but with the same result i have all the repositories enabled but cant understand what to do. i have also tried installing the dependant packages but the same "it is not going to be installed" thing turns up.

no broken packages are shown by the packet manager and sudo apt-get -f install does do any either.

PLease help me out i am a Linux noob.

---

### Post by donatell0 on 2006-09-18
Not sure, but hope this helps. 
You should first check if there is an installed version of the libplplot9 that does not match the version of the package that pplot requires. Then remove that and then try to install pplot.

---

