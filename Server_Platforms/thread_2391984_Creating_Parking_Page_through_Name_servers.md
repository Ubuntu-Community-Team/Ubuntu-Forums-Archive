---
title: "Creating Parking Page through Name servers"
date: 2018-05-15
forum: Server Platforms
---

### Post by kingdev on 2018-05-15
Hello,

i want to create a DNS server to host all expired domain names with Custom Page.

So when domain expire, the DNS change to expired1.exemple.com, expired2.exemple.com

the server who host those DNS will show a Custom Page created by me.

Do you have an idea how to do that.

---

### Post by SeijiSensei on 2018-05-15
When a domain expires, it either becomes unreachable or is picked up by someone new.  Are you talking about a local DNS server that answers queries for those expired domains within a network you manage?

---

### Post by kingdev on 2018-05-16
[COLOR=#1A1A1A]PS: i'am a cctld registrar so expired domains remains active for one month.[/COLOR]

---

### Post by SeijiSensei on 2018-05-17
If by a "parking page" you mean a web page that announces that the domain has expired, you need to run a webserver and direct requests for the expired domains there by changing the A records in the expired domain's zone file to point to the web server.

```

@    IN SOA example.com root.example.com {
     IN A   ip.addr.of.webserver

     IN NS ...
     IN MX ...
)
www IN A ip.addr.of.webserver

```

You can use the default Apache configuration in Ubuntu to handle these requests.  Just replace the file /var/www/html/index.html with your own "landing page."

---

