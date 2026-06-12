---
title: "Issue connecting to repositories"
date: 2007-05-03
forum: Repositories &amp; Backports
---

### Post by karmak.diesel on 2007-05-03
Is anyone else having an issue when trying to connect to the default configured repositories or is it my system configuration?  i tried to run system update and received:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007e-0ubuntu0.7.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007e-0ubuntu0.7.04_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.59.20_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.59.20_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_0.76.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_0.76.1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_0.76.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_0.76.1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_0.76.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_0.76.1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_0.76.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_0.76.1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.59.20_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.59.20_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by flavioamieiro on 2007-05-03
I'm having the same problem here.

When I do 

```
sudo apt-get update
```

i get these results:

```

Err http://br.archive.ubuntu.com feisty Release.gpg                            
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com feisty/main Translation-pt_BR                 
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com feisty/restricted Translation-pt_BR           
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com feisty/universe Translation-pt_BR             
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com feisty/multiverse Translation-pt_BR           
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Obtendo:1 http://security.ubuntu.com feisty-security Release.gpg [191B]        
Ign http://security.ubuntu.com feisty-security/main Translation-pt_BR          
Obtendo:2 http://download.tuxfamily.org feisty Release.gpg [189B]              
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-pt_BR
Err http://br.archive.ubuntu.com feisty-updates Release.gpg                    
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com feisty-updates/main Translation-pt_BR         
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com feisty-updates/restricted Translation-pt_BR   
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Ign http://security.ubuntu.com feisty-security/restricted Translation-pt_BR    
Ign http://security.ubuntu.com feisty-security/universe Translation-pt_BR      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-pt_BR    
Atingido http://security.ubuntu.com feisty-security Release                    
Atingido http://download.tuxfamily.org feisty Release                          
Atingido http://security.ubuntu.com feisty-security/main Packages              
Atingido http://download.tuxfamily.org feisty/avant-window-navigator Packages
Atingido http://security.ubuntu.com feisty-security/restricted Packages 
Atingido http://security.ubuntu.com feisty-security/main Sources               
Atingido http://security.ubuntu.com feisty-security/restricted Sources         
Atingido http://download.tuxfamily.org feisty/avant-window-navigator Sources   
Atingido http://security.ubuntu.com feisty-security/universe Packages          
Atingido http://security.ubuntu.com feisty-security/universe Sources    
Atingido http://security.ubuntu.com feisty-security/multiverse Packages 
Atingido http://security.ubuntu.com feisty-security/multiverse Sources  
Obtendo:3 http://ubuntu.beryl-project.org feisty Release.gpg [191B]                       0
Ign http://ubuntu.beryl-project.org feisty/main Translation-pt_BR                         
Atingido http://ubuntu.beryl-project.org feisty Release                                   
Atingido http://ubuntu.beryl-project.org feisty/main Packages                             
Baixados 193B em 11s (16B/s)                                                              
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-pt_BR.bz2  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-pt_BR.bz2  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-pt_BR.bz2  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-pt_BR.bz2  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-pt_BR.bz2  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-pt_BR.bz2  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Lendo Lista de Pacotes... Pronto
W: Alguns arquivos de índice falharam no download, eles foram ignorados ou os antigos foram usados em seu lugar.

```

It's in portuguese but I can tell you that "Conexão recusada" means "Connection refused"

I can't install anything now, since it won't connect to get new packages (i've tried through synaptic and - obviously - it didn't work either).

I'm new to linux, and yet this is the first time I can't find an answer for my problems without having to post. This community REALLY works.

Anyways, hope someone can help me

---

### Post by p3nn on 2007-05-15
I've had the same prob as well with my laptop. After some searching and asking on other forums someone gave the the idea of adding the isp's dns's in System->Administration->Network->DNS
That seems to have fixed it my end and hopefully will do the same for you. If you don't know your isp's dns's you can always use the ones from opendns which are 208.67.222.222 and 208.67.220.220 respectively

---

### Post by p3nn on 2007-05-17
The other possibility is that you have installed a proxy like anonproxy which is interfering anything using apt-get. Try opening up synaptic package manager and putting proxy into the search dialog and seeing what shows as installed. If anonproxy is installed then try uninstalling and restarting

---

### Post by dwai on 2007-06-01
> **p3nn said:**
> The other possibility is that you have installed a proxy like anonproxy which is interfering anything using apt-get. Try opening up synaptic package manager and putting proxy into the search dialog and seeing what shows as installed. If anonproxy is installed then try uninstalling and restarting
anon-proxy is indeed an issue..
one may use sudo apt-get autoremove anon-proxy   to remove it...  but some config files still remain to be purged and then may use dpkg --purge anon-proxy and then restart networking to solve the issue (connection refused)

---

