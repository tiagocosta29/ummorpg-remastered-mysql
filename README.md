# This is a fork from the original ummorpg remastered mysql plugin to support the UMMORPG2D package
OG REP Link https://github.com/lukehoulihan/ummorpg-remastered-mysql

# UMMORPG2D-remasterd-mysql drop in replacement script
This project is a drop in replacement for the default `Database.cs` script in UMMORPG2D Remastered.
Please be advised -
* This script was created for UMMORPG2D Remastered 
* This is a free add-on.  I will not troublshoot issues for you.  If you see a bug, log the issue and I'll fix it if I have time.  Better yet, fix it yourself and open a pull request.
* No optimizations or improvements where made to this script - this is a 1:1 conversion of existing logic.  The default database design is so poor that there isn't much to be done without a total re-write.  (No offense intended to Vis2k, it's good enough to get a beginner started).

## How to contribute
Send me pull requests if you want to see some changes.

Open issues if you find a bug.

Send me a tip if you use Brave and you want to give back.

## Installation instructions
### 1. Backup your project
This is your only warning.

### 2. Setup MySQL
Using [docker](https://www.docker.com/) because it's dead simple. 
1. [Install docker](https://docs.docker.com/install/)
2. Pull down and run the [MySQL](https://hub.docker.com/_/mysql/) or [MariaDB](https://hub.docker.com/_/mariadb) docker images.  Either will work.
3. No need to create any schema or tables, the script will auto-generate everything.  Just note down the username/password you passed into the docker container.

Using Xampp
1. [Install Xampp](https://www.apachefriends.org/index.html)
2. Start MySQL service
3. Default user is root with no password needed (make sure to change this when going to production!)

### 3. Install in your project
1. Launch Unity and open your project.
2. Download or pull down this repo.
3. Drag and drop the folder `MySQL`(under plugins) to `Assets-> uMMORPG -> Plugins`
4. **You'll get some errors, don't panic.** These show up because Unity doesn't know how handle .net assembly dependency versions that are higher than the listed requirements.
5. Select the .net assembly `MySqlConnector` under `Assets/uMMORPG/Plugins/MySQL/MySqlConnector/` and uncheck the `Validate References` property under `General` in the inspector. Click `Apply` in the inspector.
6. Right click `MySqlConnector` in the project window and select `Re-import`
7. Do the same to `System.Memory` and `System.Threading.Tasks.Extensions`.  Don't forget to re-import after each change.
8. If you're still seeing errors double check that `Validate References` is unchecked on all 3, clear your console, then Re-import `MySqlConnector`.
9. Next Drag and drop the `Database.cs` file from this repository to `Assets-> uMMORPG -> Scripts` in your project. Select `Yes` to overwrite the existing file.
### 4. Apply to your scene
1. Load up your level scene and select the `NetworkManager` in the hierarchy.
2. You'll see a `Script missing` message where the database script used to be.
3. Drag and drop the new `Database` script into the missing script field. 
4. The component properties will populate allowing you to enter the user id and password you used to set up mysql earlier.
5. Hit play and test it out.
