---
title: "How to make script insert code below certain Words / lines?"
date: 2012-01-02
forum: Server Platforms
---

### Post by kembar4 on 2012-01-02
Well guys, I'm modifying a script to create multiple users for ruTorrent.

Anyways, i need help on this part.

Basically, along this code, i would be asked to enter a port

```

get_scgi_port() {
	scgi_mount="/rutorrent/$user_name"
	read -p "SCGi Port: " scgi_port

	while [[ $scgi_port -lt 1024 || $scgi_port -gt 65535 || $scgi_port -eq 5000 ]]; do
		echo -e "\n${bldred}- Invalid Port${rst}"
		read -p "SCGi Port: " scgi_port
	done
}
```

And along this code, the port would be inserted into a config text file.

```
httpd_add_scgi() {
	if [[ $webserver = 'lighttpd' ]]; then
		echo "SCGIMount $scgi_mount 127.0.0.1:$scgi_port" THIS IS THE PART THAT NEEDS TO BE MODIFIED AND BE PUT BELOW A CERTAIN LINE / WORD >> /etc/lighttpd/lighttpd.conf
	fi
	sudo -u $user_name echo "network.scgi.open_port = 127.0.0.1:$scgi_port" >> /home/$user_name/.rtorrent.rc
	echo -e "${bldred}-${rst} SCGi Mount ..........[${bldpur} CREATED ${rst}]"
	echo -e "${bldred}-${rst} SCGi Port ...........[${bldpur} $scgi_port ${rst}]\n"
}
```

So as you can see below, i want the iput to be pasted in this format, below the "scgi.server =(" line. Also this mustn't produce any errors in the sense that i would be running this script to add more entries, more than once. Each entries would be seperated of course.

This is how the output should look like:

```
scgi.server = (
"/var/www/rutorrent/RPC2" => # RT_DIR
 ( "127.0.0.1" =>
  (
   "host" => "127.0.0.1",
   "port" => 5000,
   "check-local" => "disable"
  )
 ),
"/var/www/rutorrent/RPC3"=>
 (
   "127.0.0.1" =>
  (
   "host" => "127.0.0.1",
   "port" => 5001,
   "check-local" => "disable"
  )
 )
) 
```

---

