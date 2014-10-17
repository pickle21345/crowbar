## Crowbar (Levye) - Brute forcing tool for pentests


### What is it?

**Crowbar** (crowbar) is brute forcing tool that can be used during penetration tests. It is developed to support protocols that are not currently supported by thc-hydra and other popular brute forcing tools. 

Currently **Crowbar** supports  
- OpenVPN
- SSH private key authentication
+ VNC key authentication
* Remote Desktop Protocol (RDP) with NLA support

### Installation

First you shoud install dependencies
```
 # apt-get install openvpn freerdp-x11 vncviewer
```

Then get latest version from github  
```
 # git clone https://github.com/galkan/crowbar 
```

Attention: Rdp depends on your Kali version. It may be xfreerdp for the latest version.

### Usage

**-h**: Shows help menu.

**-b**: Specify the target service

**-s**: Specify the target ip address.

**-S**: Specify the file name which is stores target ip address.

**-u**: Specify the username.

**-U**: Specify the file which stores username.

**-n**: Specify the thread count.

**-l**: Specify the file which stores log. Deafault file name is crwobar.log which is located in your current directory

**-o**: Specify the output file which stores the successfully attempt.

**-c**: Specify the password.

**-C**: Specify the file which stores passwords.

**-t**: specify the timeout value.

**-p**: 

**-k**: 

**-m**: 

**-d**: 

**-v**: Specify the verbose mode which is shows all the attempts including fail.


If you want see all usage options, please use crowbar --help 

**Brute forcing RDP**  
```
crowbar.py -b rdp -s 192.168.2.182/32 -u admin -c Aa123456
```

```
crowbar.py -b rdp -s 192.168.2.211/32 -U /root/Desktop/userlist -c passw0rd
```

```
crowbar.py -b rdp -s 192.168.2.250/32 -u localuser -C /root/Desktop/passlist
```

```
crowbar.py -b rdp -s 192.168.2.0/24 -U /root/Desktop/userlist -C /root/Desktop/passlist -d
```

**Brute forcing SSH**  
```
crowbar.py -b sshkey -s 192.168.2.105/32 -u root -k /root/.ssh/id_rsa
```

```
crowbar.py -b sshkey -s 192.168.2.105/32 -u root -k /root/.ssh/
```

```
crowbar.py -b sshkey -s 192.168.2.0/24 -u root -k /root/.ssh/ -d
```

Attention: If you want, you can specify the key directory with -k option. Crowbar will use all the files under this directory for brute force. For instance;

 ``# crowbar.py -k /root/.ssh``

**Brute forcing VNC server**  

```
crowbar.py -b vnckey -s 192.168.2.105/32 -p 5902 -c /root/.vnc/passwd 
```

**Brute forcing OpenVPN**  

```
crowbar.py -b openvpn -s 198.7.62.204/32 -p 443 -m /root/Desktop/vpnbook.ovpn -k /root/Desktop/vpnbook_ca.crt -u vpnbook -c cr2hudaF
```

### Example Output

 Once you have executed crowbar, it generates 2 files for logging and result. Default log file name is crowbar.log which is    
 located in your current directory. If you don't want use default log file, you should use -l log_path. After that you can   
 observe crowbar operations. For instance;

 # cat crowbar.log

 # cat crowbar.out


#### Thanks To
 
 - Bahtiyar Bircan
 - Ertuğrul Başaranoğlu
