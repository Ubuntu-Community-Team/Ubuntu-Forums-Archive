---
title: "Creating a user using PHP"
date: 2008-09-26
forum: Server Platforms
---

### Post by benoybose on 2008-09-26
How can we create a Linux user via PHP code. The script must be executed by Apache2 via web request.

Can we do
sudo adduser <username>

in exec function of PHP ?
Then how can we specify the password and other parameter. Or can we add a user using a single command line

Can we specify the home directory along when user is created?

Help needed?

---

### Post by Titan8990 on 2008-09-26
I am no expert on PHP but I can tell you one thing:

Sudo in scripts does not work. The script will need to be ran as root opening up a big security hole on your server. 

You may want to come up with an alternate method of adding users. Possibly keep users for the website in a mysql database instead of local users. That seems to be the more popular method.

Also, adduser from my experience has been interactive where as useradd is not. There may be arguments to add to adduser that would cause it not be interactive, however, my quick look at the man pages did not show this as an option.

---

