---
title: "New to Ubuntu Pro"
date: 2024-11-07
forum: Security
---

### Post by mongo42 on 2024-11-07
Hi All,

I just activated Ubuntu Pro on a new installation, and have a quick question.  I connected my computer via the access code given through "Software & Updates --> Enable Ubuntu Pro" and entering it online.  It came back and said that the code was valid in green.  I then entered the command given to connect my computer, which it did successfully (as far as I can tell).  Then I noticed the "Verify" button in the window where I entered the code.  I clicked on "Verify" and the green "Valid Code" changed to a red "Invalid Code".  My question is, is my clicking the "Verify" button *after* the CLI activation problematic, or did it simply change to "Invalid Code" since it was a one-time code that became invalid when I connected my machine?  In other words, did my installation of Pro complete successfully?  Thanks!

Mongo

---

### Post by Tadaen_Sylvermane on 2024-11-07
I think the command ```
sudo pro status
``` should return whether or not it's enabled properly. Also assuming you are on the standard Ubuntu you should have a live patch icon up in the bar on top on the right. Whether or not it's enabled should be clear from this command.

---

### Post by mongo42 on 2024-11-07
Thank you for the quick reply.  There is not an Icon in the upper right (unless I'm just not seeing it - Forrest through the trees and all that), but connecting from the CLI gave:

[B]Enabling Ubuntu Pro: ESM Apps
Ubuntu Pro: ESM Apps enabled
Enabling Ubuntu Pro: ESM Infra
Ubuntu Pro: ESM Infra enabled
Enabling Livepatch
Livepatch enabled
This machine is now attached to 'Ubuntu Pro - free personal subscription'

SERVICE          ENTITLED  STATUS       DESCRIPTION
anbox-cloud      yes       disabled     Scalable Android in the cloud
esm-apps         yes       enabled      Expanded Security Maintenance for Applications
esm-infra        yes       enabled      Expanded Security Maintenance for Infrastructure
fips             yes       disabled     NIST-certified FIPS crypto packages
fips-updates     yes       disabled     FIPS compliant crypto packages with stable security updates
livepatch        yes       enabled      Canonical Livepatch service
ros              yes       disabled     Security Updates for the Robot Operating System
usg              yes       disabled     Security compliance and audit tools

NOTICES
Operation in progress: pro attach

For a list of all Ubuntu Pro services, run 'pro status --all'
Enable services with: pro enable <service>

     Account: [EMAIL="xxxxxxxxx@stratusiq.net"]xxxxxxxxx@stratusiq.net[/EMAIL]
Subscription: Ubuntu Pro - free personal subscription[/B]

and the command "sudo pro status" gives:

[B]SERVICE          ENTITLED  STATUS       DESCRIPTION
anbox-cloud      yes       disabled     Scalable Android in the cloud
esm-apps         yes       enabled      Expanded Security Maintenance for Applications
esm-infra        yes       enabled      Expanded Security Maintenance for Infrastructure
fips             yes       disabled     NIST-certified FIPS crypto packages
fips-updates     yes       disabled     FIPS compliant crypto packages with stable security updates
livepatch        yes       disabled     Canonical Livepatch service
ros              yes       disabled     Security Updates for the Robot Operating System
usg              yes       disabled     Security compliance and audit tools

For a list of all Ubuntu Pro services, run 'pro status --all'
Enable services with: pro enable <service>

     Account: [EMAIL="xxxxxxxxxx@stratusiq.net"]xxxxxxxxxx@stratusiq.net[/EMAIL]
Subscription: Ubuntu Pro - free personal subscription


[/B]Thanks!

EDIT: As soon as I enabled Livepatch, the icon appeared (funny how that works)... Though I do not see a process in the System Monitor? Is it included in the "Update Notifier" process (which *is* active)?

---

### Post by deadflowr on 2024-11-07
It would be called canonical-livepatchd.

---

### Post by mongo42 on 2024-11-07
OK... it's official: I'm confused.  I cannot find anything that would suggest that the pro is not working correctly (no error messages in the CLI, the livepatch icon is displayed in the upper right, etc), but the process "canonical-livepatchd" is not listed as being active.  I have rebooted, manually stopped and then restarted the livepatch process via Settings, all to no avail.  Thanks!

EDIT: I had a thought (It happens from time to time).  Given that the livepatch process only checks for updates periodically, would it only load itself when it is checking, and remove the process?  I'm just scraping the bottom of the barrel trying to understand why looking at the active processes it is not listed...

---

### Post by deadflowr on 2024-11-07
It's not active unless actually in use.
You can check the status with
```
canonical-livepatch status --verbose
```

---

### Post by mongo42 on 2024-11-07
Thank you so much!

---

