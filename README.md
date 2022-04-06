# esp_wifimanager
connecting esp without hard coding ssid and password


In this program, we are going to walk through ” how to Change ESP8266 WiFi credentials without uploading code from Arduino IDE”, We will update WiFi Credential wirelessly and store the same credentials in the EEPROM memory of the ESP8266  using a really awesome library “EEPROM.h“. We are going to develop an Arduino Program and a library, Which First Reads the WiFi Credentials from the EEPROM, and tries to connect to that; If the WiFi is not available or there are no credentials stored in the EEPROM, ESP8266 will Acts an Accespoint and creates Hotspot which will allow us to connect and modify the WiFi credential. Then it connects to the freshly configured WiFi Credentials. It will only take a couple of minutes to go through these steps.



If you have hard-coded values in your sketch, if you change your WiFi router or want to bring your device to somewhere else, you are going to need to re-program your esp8266, which isn’t ideal!

It also makes your sketches less sharable, as you probably will want to replace your SSID and Password with placeholders before uploading to somewhere public like GitHub and anyone who is using your code is going to have to update the code before they can use it on their network. This is why we should have WiFi Provisioning in our solutions. Even all IoT Devices that are available in the market have this WiFi Provisioning Feature.

**What is WiFi Provisioning???**
Provisioning IoT products, that do not have a keyboard and display as a user interface, in a simple and robust way is a significant challenge.

Wi-Fi provisioning is the process of connecting a new Wi-Fi device (station) to a Wi-Fi network. The provisioning process involves loading the station with the network name (often referred to as SSID) and its security credentials. In this process, The target device will first act as an access point and allow us to connect and modify the WiFi credential.

**Program & Source Code: Change ESP8266 WiFi credentials without uploading code**
The Program is designed to follow the below steps.

On ESP8266 boot, it is set up in Station mode, and Read the pre-registered SSID and password combination and tries to connect to the same.
If this process fails, it sets the ESP into Access Point mode and creates Open Wifi(Not protected with Password);
This open wifi will allow the user to connect Using any Wi-Fi enabled device with a browser
After establishing a connection with the Access point, you can go to the default IP address 192.168.4.1 to open a web page that allows user to configure your SSID and password, (port and ip. if neccessary) ;
Once a new SSID and password is set, the ESP reboots and tries to connect;
If it establishes a connection, the process is completed successfully. and executes the Blinking of LED Code with 1000 milliseconds delay.
If the connection fails again, it will be set up as an Access Point to configure the new SSID and Password.
