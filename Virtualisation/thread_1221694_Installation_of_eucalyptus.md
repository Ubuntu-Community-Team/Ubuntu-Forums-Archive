---
title: "Installation of eucalyptus"
date: 2009-07-24
forum: Virtualisation
---

### Post by winter2009 on 2009-07-24
"sudo euca_conf -addnode 192.168.1.188
/var/lib/eucalyptus
First, please run the following commands on '127.0.1.1':

sudo apt-get install eucalyptus-nc
sudo tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEArFrN6pEgwHClMuxoN8XzlDAELUHPLk3xcShmTLjqZzIM+yew40shcf87+8HONc3z5oTm6GXS6RPl13PEnOqk61t7fo6xCh7ODIlTmDWtluIF3pk5t4bPOW+Xg3tI6ywhQJnAYvkg5hJstAvwvq3wtDr2TKqONfLbOAMCVzyLvCH3sY7ILSKgK45p3evo3CDsNajktfs2geifmyHnfN/vL8JOyHi8PmDryxrcsAqdls9tgdH8qDQE8rZrEkky5Uqn3Wi0pcbDXBH92J7u4qLnFR2NzPEQj+5vHdWv+fnsf/vnnCeDq9/tGJ5A9UZBVhB2MdpT8hnM5lt7sNQDnbFJGQ== eucalyptus@test-ubuntu
EOT

hit return to continue
^C
"

I have been stopped here for quite a while. Search through the internet but not find any detail solutions about this. Can anyone please suggest me how shall I go through this "add node" stage? Thanks a lot.

By the way, I want to put the cloud controller, cluster controller and node controller together on one machine. Is it possible to do this?

---

