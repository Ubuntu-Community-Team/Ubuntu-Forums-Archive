---
title: "Linux Server / Vista Client $recyle.bin issue"
date: 2009-05-06
forum: Server Platforms
---

### Post by pigboy on 2009-05-06
Hello.

I am running the new 9.04 as a server on my network. I am sharing out the videos, pictures, documents and music folders to my vista based notebook. 

Specifically, I have modified my vista in the following way:
My Pictures and My Music folders have been moved to \\UBUNTU_SERVER\share2 and \\UBUNTU_SERVER\share3 respectively.

I did this by right clicking on the items in my start menu and choosing properties>location>move and choosing the network path to the location I wish these folders to be stored.

Main reason for this is to keep my notebook lite and clean and all my data on the server machine.

Enter the issue. Whenever I open or select to empty my recyle bin on the vista machine I get an error for each share saying the following:
"The Recycle Bin on \\UBUNTU_SERVER\share3 is corrupted. Do you want to empty the Recycle Bin for this drive?"

If I choose yes, it gives me a permissions error when attempting to delete desktop.ini so I have to choose no.

Anyone know how to fix this? Maybe by telling Vista to not worry about a recyle bin on these locations or something? Or do I have to just give undisclosed permissions to allow the deletion of the desktop.ini file?

Stuck. I want this setup to work, but ran into this obstacle. Any and all suggestions welcome. Successful resolution will be rewarded with an invaluable amount of gratitude, well, I'll just say thanks like a thousand times... :)

---

### Post by cariboo on 2009-05-06
The recycle bin is a windows feature, you may be able to delete files in the bin by installing [this]("http://www.fs-driver.org/index.html") driver, or use shift-delete when deleting files from a share.

---

