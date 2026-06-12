---
title: "Autenticação Squid3 no Windows AD(Active Directory)"
date: 2013-09-19
forum: Server Platforms
---

### Post by James_Carvalho on 2013-09-19
Prezados 

Estou usando o Ubuntu Server 13.04 e Squid3 e  Apache2 e Samba(version 3.6.09) e Winbind (version 3.6.9)
Não estou conseguindo autenticar  os usuários do domínio AD no SQUID3.
O comando "klist" lista a conexão com o AD (krbtgt/domínio.local@domínio.local)
quando utilizo o comando "webinfo -u" ou "webinfo -g" , lista normalmente os usuários e grupos do domínio AD.
_**Abaixo está as configurações do arquivo "SQUID.CONF"**_
[COLOR=#004080][FONT=Verdana]# /etc/squid3/squid.conf
#
#
#
# Licença: GPL - [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)
# Solicito apenas que informe a fonte original.
# 
# Descrição:
# - Arquivo para configuração do squid
#
##########################################

# Portas (padrão 3128)
#########################################[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_port 172.16.10.253:3128[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# OTIMIZANDO CONEXÕES[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#########################################[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]hierarchy_stoplist cgi-bin ?[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]###acl QUERY urlpath_regex cgi-bin \? \& \%[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]###no_cache deny QUERY[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]####hosts_file /etc/hosts[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]refresh_pattern ^ftp: 1440 20% 10080[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]refresh_pattern ^gopher: 1440 0% 1440[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]refresh_pattern . 0 20% 4320[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# Logs[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]########################################[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#logformat combined %>a %ui %un [%tl] "%rm %ru HTTP/%rv" %Hs %<st "%{Referer}>h" "%{User-Agent}>h" %Ss:%Sh[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#access_log /var/log/squid3/access.log combined[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]access_log /var/log/squid3/access.log [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]cache_log  /var/log/squid3/cache.log[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# ACLs[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#########################################[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# acls de origem[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# =======================================[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# qualquer rede[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#acl all src 0.0.0.0/0.0.0.0[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# rede loopback[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl localhost src 127.0.0.1/32[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# rede dmz (rede servidores)[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#acl dmz src 192.168.0.0/24[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# rede administrativo (rede setor administrativo)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl administrativo src 172.16.10.0/24[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# rede acadêmica (rede setor acadêmico)[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#acl academica src 172.16.0.0/24[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]### admins (IPs com acesso administrador do squid - não usam proxy para navegar)[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#acl admins src 172.16.10.180/32[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# acls de destino[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# =======================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl allDest dst 0.0.0.0/0.0.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl to_localhost dst 127.0.0.0/8[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# acls de portas[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# =======================================[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# portas seguras[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl SSL_ports port 443 563[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# demais serviços[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 80 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# http[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 8080 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# tomcat[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 8443 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# tomcat - ssl[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 10000 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# webmin[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 21 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# ftp[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 443 563 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# https, snews[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 70 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# gopher[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 210 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# wais[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 1025-65535 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# unregistered ports[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 280 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# http-mgmt[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 488 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# gss-http[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 591 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# filemaker[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 631 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# cups[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 777 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# multiling http[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#acl Safe_ports port 901 # SWAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 4500 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# Biblioteca USP dedalus[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 2083 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# CPANEL[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 2631 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# Conectividade Social[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 1494 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# Sigov[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl Safe_ports port 8333 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# WMWARE SERVER[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# acls default squid[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ========================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl purge method PURGE[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl CONNECT method CONNECT [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access allow manager localhost[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access deny manager[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access allow purge localhost[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access deny purge[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# acls de segurança[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# =======================================[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# proteção do cache[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl manager proto cache_object[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# ========================================[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# 1 - acl controlar sites (sites-proibidos)[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ----------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl sites_deny dstdomain -i "/etc/squid3/acls/sites-proibidos"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl sites_allow dstdomain -i "/etc/squid3/acls/sites-permitidos"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl caixa dstdomain -i .caixa.gov.br[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# 2 - acl controlar palavras de sexo, baixo calão, etc[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ----------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl palavras_deny url_regex -i "/etc/squid3/acls/palavras-deny"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl palavras_allow url_regex -i "/etc/squid3/acls/palavras-allow"[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# 3 - acl controlar horário de expediente[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ----------------------------------------[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#acl horario_allow url_regex -i "/etc/squid3/horario_allow"[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#acl fora_expediente time MTWHFA 20:01-23:59[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#acl fora_expediente2 time MTWHFA 00:00-05:59[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# 4 - acl liberacao Windowsupdate [/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ----------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl update dstdomain -i Windowsupdate.microsoft.com au.download.Windowsupdate.com[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# acls de sites locais[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# =======================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl sites_locais dst 192.168.0.100[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#acl sites_locais dstdomain 192.168.0.100[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# HTTP ACCESS[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]##########################################[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# regras das acls de origem[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ========================================[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# libera os administradores[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#http_access allow admins[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# regras das acls de portas[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ========================================[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# bloqueia todas as portas não listadas[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access deny !Safe_ports[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# bloqueia conexões das portas seguras não listadas[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access deny CONNECT !SSL_ports[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# regras das acls de controle (bloqueio e políticas de rede)[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ========================================[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]http_access allow all AuthorizedUsers[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# 1 - controle de acessos especiais[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ----------------------------------------[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# bloqueia tudo com exceção do arquivo excecao[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access allow update [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access allow liberaexe[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# 2 - controle de acesso de sites proibidos[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ----------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access deny sites_deny !sites_allow[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# 3 - controle de acesso da acl de palavras de sexo, baixo calão, etc[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ---------------------------------------[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# bloqueia todas as palavras da lista de proibidas com exceção das[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# palavras liberadas[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access deny palavras_deny !palavras_allow[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# 4 - controle de horário de expediente[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ----------------------------------------[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# bloqueia utilização fora do expediente[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#http_access deny !horario_allow fora_expediente[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#http_access deny !horario_allow fora_expediente2[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# 5 - controle de acesso ao site da caixa (Conectividade social)[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ---------------------------------------[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# permite acesso direto ao site da caixa, sem restrições[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access allow caixa[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]always_direct allow caixa[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# 6 - controle de acesso da acl de palavras de sexo, baixo calão, etc[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# ---------------------------------------[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# bloqueia todas as palavras da lista de proibidas com exceção das[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# palavras liberadas[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access deny palavras_deny !palavras_allow[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# HTTP REPLY ACCESS[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#########################################[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_reply_access allow all[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# ICP ACCESS[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#########################################[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]icp_access allow all[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# MISS ACCESS[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#########################################[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]miss_access allow all[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# MODO DE FTP PASSIVO[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#########################################[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#ftp_passive on[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# DNS[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#########################################[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]dns_nameservers 172.16.10.254[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# SNMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl snmpro snmp_community local[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]snmp_access allow snmpro all[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]snmp_port 3401[/FONT][/COLOR]

[COLOR=#004080][FONT=Verdana]# CONFIGS Diversas[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]########################################[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# Email do administrador[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]cache_mgr [email]leandro@leandromoreira.eti.br[/email][/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# Host visível[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]visible_hostname proxy.dominio.local[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# Linguagem dos erros[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]error_directory /usr/share/squid3/errors/Portuguese[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# Evita que sejam feitos coredumps.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]coredump_dir /var/spool/squid3[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]# Numero de arquivos de log rotacionados a guardar.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]logfile_rotate 4
[/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# Autenticação no Windows 2008[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]auth_param ntlm children 30[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-basic[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]auth_param basic children 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]auth_param basic realm Squid proxy-caching web server[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]auth_param basic credentialsttl 2 hours[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]acl AuthorizedUsers proxy_auth REQUIRED[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]http_access allow all AuthorizedUsers[/FONT][/COLOR]




_***Abaixo está as configurações do arquivo SMB.CONF**_
[COLOR=#000000][FONT=Verdana]unix charset = ISO-8859-1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]workgroup = DOMAIN [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# Domínio a qual o servidor pertence[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]netbios name = PROXYVM [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# Nome netbios do servidor[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]server string = proxyvm [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# Alias para o servidor[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]log level = 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]load printers = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]log file = /var/log/samba/log.%m[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]max log size = 500[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]realm = dominio.local [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# Domínio do servidor[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]security = ads[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]auth methods = winbind[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#password server = win2003.dominio.local # Endereço do servidor de autenticação nome/ip[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]password server = 172.16.10.254 [/FONT][/COLOR][COLOR=#004080][FONT=Verdana]# Endereço do servidor de autenticação nome/ip[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]winbind separator = +[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]encrypt passwords = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]printcap name = cups[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]winbind cache time = 15[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]winbind enum users = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]winbind enum groups = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]winbind use default domain = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]idmap uid = 10000-20000[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]idmap gid = 10000-20000[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]local master = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]os level = 233[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]domain master = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]preferred master = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]domain logons = no[/FONT][/COLOR]
[COLOR=#004080][FONT=Verdana]#wins server = 172.16.20.150 # Só deve ser descomentado se o servidor Windows for um 2003[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]dns proxy = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ldap ssl = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]printing = cups[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]disable spoolss = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]show add printer wizard = no[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]template shell = /bin/bash[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]template homedir = /home/%U
[/FONT][/COLOR]
Abaixo está as configurações do arquivo [I]/etc/init.d/winbind que foi habilitado
[/I][COLOR=#000000][FONT=Verdana]chgrp proxy $PIDDIR/winbindd_privileged/ || return 1
[/FONT][/COLOR]
[U][B]
Abaixo está as configurações do **/etc/krb5.conf**[COLOR=#000000][FONT=Verdana] [/FONT][/COLOR][/B][/U]

[COLOR=#000000][FONT=Verdana][libdefaults][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ticket_lifetime = 24000[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]default_realm = DOMINIO.LOCAL[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]dns_lookup_realm = false[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]dns_lookup_kdc = false[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana][realms][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]DOMINIO.LOCAL = {[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]kdc = 172.16.10.254[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]admin_server = 172.16.10.254:749[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]default_domain = 172.16.10.254[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]}[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana][domain_realm][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana].dominio.local = DOMINIO.LOCAL[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]dominio.local = DOMINIO.LOCAL[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana][login][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]krb4_convert = true[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]krb4_get_tickets = false[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana][logging][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]kdc = FILE:/var/log/krb5kdc.log[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]admin_server = FILE:/var/log/kadmin.log[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]default = FILE:/var/log/krb5lib.log[/FONT][/COLOR]


Foi sincronizado a data e hora do  Server_Proxy com o Server_AD(Activer Directory) através do comando:
[B]# ntpdate Server_AD
[/B][COLOR=#000000][FONT=Verdana]
Já foi adicionado o Server_PROXY no domínio AD através do comando:
[/FONT][/COLOR]**# net ads join DOMINIO -U administrador%SENHA_DO_ADMINISTRADOR**
[COLOR=#000000][FONT=Verdana]Using short domain name -- DOMINIO[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Joined 'PROXYVM2' to realm 'dominio.local' [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

---

