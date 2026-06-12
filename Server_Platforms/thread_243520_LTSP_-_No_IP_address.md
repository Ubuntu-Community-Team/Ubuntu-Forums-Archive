---
title: "LTSP - No IP address"
date: 2006-08-25
forum: Server Platforms
---

### Post by Canellas on 2006-08-25
Hi,

I configured LTSP, but when I boot the terminal, I get a "No IP address" message, when it tries to find the 'dchp' server.

My /etc/dhcp3/dhcpd.conf is like this:
"
# Arquivo de configuração do servidor DHCP para o LTSP 4.2
# Por Carlos E. Morimoto


shared-network WORKSTATIONS {

    subnet 192.168.0.0 netmask 255.255.255.0 {

	default-lease-time            21600;
	max-lease-time                21600;

	# Configure as opções abaixo adicionando os endereços da sua rede: 

	# Mascara de sub-rede:
	option subnet-mask            255.255.255.0;

	# Endereço de broadcast (é sempre o último endereço da rede, como em 192.168.0.255)
	option broadcast-address      192.168.0.255;

	# Default gateway (o micro que está compartilhando a conexão e do DNS da rede)
	option routers                192.168.0.1;
	option domain-name-servers    192.168.0.1;

	# Esta opção faz com que o servidor dhcp aceite apenas os clientes do
	# terminal server, não conflitando com um servidor dhcp já existente.

	deny unknown-clients;

	# Caso prefira que o servidor DHCP dê IPs de rede local também para os
	# demais micros da rede, que não estão cadastrados como terminais, comente
	# a linha acima e descomente a linha abaixo, informando a faixa de endereços
	# que será usada pelos clientes que não estejam cadastrados como terminais:

	# range 192.168.0.100 192.168.0.201;


	# IMPORTATE!! Substitua o "192.168.0.10" pelo endereço IP do servidor 
	# Kurumin (esta máquina), se este endereço estiver errado o LTSP não 
	# funcionará! Repita o mesmo endereço na opção "next-server", ela é um 
	# workaround para um bug do dhcpd 3.03:

	option root-path	"192.168.0.1:/opt/ltsp/i386";
	next-server    		 192.168.0.1;

    }

}



group   {

	use-host-decl-names       on;
#        option log-servers        192.168.0.1;

	# Aqui vão as configurações dos terminais, cada terminal deve
	# ser configurado com um endereço IP diferente e com o endereço 
	# MAC de sua placa de rede.
 
	# Para saber o endereço MAC de cada terminal, basta dar um boot
	# Com o disquete do rom-o-matic, ele mostrará o endereço MAC
	# logo no início do boot.

	# Este endereço é único, exclusivo de cada placa de rede, é através
	# dele que o servidor sabe qual terminal é qual. 

	# Adicione mais terminais caso necessário copiando e colando as linhas:

    host kent {
        hardware ethernet     00:E0:7D:A9:3B:DF;
        fixed-address         192.168.0.2;
        filename              "/tftpboot/lts/vmlinuz-2.6.17.8-ltsp-1";
    }
}
"


My '/etc/hosts' is like this:
"
# /etc/hosts, configurado para o LTSP 4.2

127.0.0.1  localhost wayne

# Você pode adicionar aqui os endereços IP e os nomes correspondentes 
# de cada terminal, caso queira utilizar mais de 8 terminais.

# IMPORTANTE: A primeira linha deve conter o endereço IP e o nome 
# (definido durante a configuração da rede) do servidor, ou seja, 
# desta máquina. Se o nome for diferente do definido na configuração 
# da rede, as estações não sequirão montar o sistema de arquivos do 
# LTSP via NFS e travarão no boot. 

192.168.0.1 wayne
192.168.0.2 kent


# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

"


My '/etc/hosts.allow' is:
"
# /etc/hosts.allow para o LTSP 4.2

# Esta configuração permite que todos os micros da rede local utilizem
# os serviços usados pelo LTSP.
# Altere o "192.168.0." caso você esteja utilizando outra faixa de
# endereços na sua rede:

ALL : 127.0.0.1 192.168.0.0/24


#bootpd:     0.0.0.0
#in.tftpd:   192.168.0.
#portmap:    192.168.0.

"


My '/etc/exports' is:
"
# /etc/exports, para o LTSP 4.2 

# Altere o "192.168.0.0" caso a sua rede utilize outra faixa de endereços IP:

/opt/ltsp/i386/		192.168.0.0/255.255.255.0(ro,sync,no_root_squash)

/var/opt/ltsp/swapfiles   192.168.0.0/255.255.255.0(rw,no_root_squash,async)

"

My '/etc/networking/interfaces' is:

"
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 162.168.0.1

auto eth1
iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


#auto eth0

auto eth0
"

And the 'ltspadmin' shows this when I choose "Show the status of all services":

"ltspcfg v0.16                                                                                                                          The Linux Terminal Server Project ([http://www.LTSP.org](http://www.LTSP.org))

Interface IP Address      Netmask         Network         Broadcast        Used 
eth0      192.168.0.1     255.255.255.0   192.168.0.0     192.168.0.255   <-----
eth1      201.17.77.122   255.255.248.0   201.17.72.0     255.255.255.255 

Service    Installed   Enabled   Running   Notes                                
dhcpd      Yes         Yes       Yes       Version 3
tftpd      Yes         Yes       Yes       No '-s' flag
portmapper Yes         Yes       Yes       
nfs        Yes         Yes       Yes       
xdmcp      Yes         Yes       Yes       gdm   Using: gdm

File                                Configured  Notes                           
/etc/hosts                          no          
/etc/hosts.allow                    no          
/etc/exports                        no          
/opt/ltsp/i386/etc/lts.conf         Yes         

Configured runlevel: 5         (value of initdefault in /etc/inittab)
   Current runlevel: 5         (output of the 'runlevel' command)

Installation dir...: /opt/ltsp

Press <enter> to return to the main menu... 
"

Can any one see what is wrong?

Thanks!

---

### Post by hela on 2006-08-26
Starting the dhcpd with "/etc/init.d/dhcpd3-server restart" always fails but "dhcpd3 -d" is okay, "dhcpd3 -d &" is not!?!?

---

### Post by Canellas on 2006-08-27
I am sorry, but I did no understand what you wrote.

If you asked if the dhcpd is running, the answer is yes, at least 'ps -ef | grep dhcp3' reports 
"
dhcpd 4662 1 0 07:07 ? 00:00:00 /usr/sbin/dhcpd3 -q eth0 -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/dhcp3/dhcpd.conf
" 

[]s

---

