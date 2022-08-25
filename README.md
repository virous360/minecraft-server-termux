# minecraft-server-termux
use termux on your phone to run a minecraft java server with whatever version you want.

NOTES :
does not require root
does not use a virtual machine inside termux 
if your phone is 4GB ram i recommend minecraft server 1.12
only works if you are on the same network unless you setup your router firewall (not covere covered here)

<h1>Overall steps : </h1>
0. settings up your phone ip as static <br>
1. setup your ssh to connect from your laptop for easy copy paste (optional) <br>
2. Get termux to run on phone boot (optional)<br>
3. installing java <br>
4. installing minecraft server <br>
5. seting up startup on boot <br>

<h2>step 0 :</h2>
in your device :  settings > connections > wifi > press on your wifi > advanced > ip settings > set to static > copy your ip to use it later ex: 192.168.1.105

<h2>step 1 :</h2>
new github repository comming soon 

<h2>step 2 :</h2>
1. Install the Termux:Boot app.

2. Go to Android settings and turn off battery optimizations for Termux and Termux:Boot applications.

3. Start the Termux:Boot app once by clicking on its launcher icon. This allows the app to be run at boot.

4. Create the ~/.termux/boot/ directory (we will add scripts later)
``` shell
mkdir ~/.termux/boot/
cd ~/.termux/boot/
```
5. if you have setup ssh :  (inside the boot directory)
``` shell
wget -O 1-runsshd.sh https://raw.githubusercontent.com/virous360/minecraft-server-termux/main/1-runsshd.sh 
``` 

<h2>step 3 :</h2>

1. run :
``` shell 
java -version
```
2. run this, changing 17 to the latest version shown in the output from the command above.
``` shell
pkg install openjdk-17
```

<h2>step 4 :</h2>
1. go to this site : http://www.mc-download.com/index.php?action=downloadfile&filename=Minecraft%20server%201.12.jar&directory=Minecraft%20Versions%20Official/Minecraft%20Server&

2. choose your version 
3. left click > right click the new link (download minecraft ....)  > copy link address 
4. run this in termux replacing with your link (```cd ~``` first)
``` shell
wget 'your-link' -O minecraft-server.jar
```
5.
``` shell
mkdir minecraft 
chmod +x minecraft-server.jar
mv minecraft-server.jar minecraft 
wget -O start_server.sh https://raw.githubusercontent.com/virous360/minecraft-server-termux/main/start_server.sh
chmod +x start_server.jar
./start_server.jar
```
6. the server WILL crash... after that run this 
``` shell
cd minecraft
apt-get install nano
nano eula.txt
```
7. change false to true 
8. ctrl-s then ctrl-x
9. you can start your server 
``` shell
cd ~
./start_server.sh 
```
<h1>done !!!</h1>

you can setup ngrok or other services to make it publically available.
