# nokia-weight-sync
Get weight from Nokia Health update to Garmin Connect or Smashrun.

![nokia-weight-sync-logo](logo.png)

## Installation

1. Download / clone the repository.

2. Satisfy the following requirements:

    - Python 3.X
    - Python libraries: arrow, requests, requests-oauthlib
    
3. [Register](https://developer.health.nokia.com/partner/add) an application with Nokia Health and obtain a consumer key and secret.

## Usage

1. On first run you need to set-up your Nokia Health consumer key and secret:

        ./nokia-weight-sync.py -k CONSUMER_KEY -s CONSUMER_SECRET setup nokia
        
2. Following the instructions and enter your oauth_verifier.

3. Verify that your last measurement group is being displayed and your Nokia credentials are saved to ```config.ini```.

4. Register one or more destination services:

    - Register your Garmin Connect credentials and sync your last measurement (provide GC password when asked):

            ./nokia-weight-sync.py -k user@example.com setup garmin
            
    - Register your Smashrun API key and following the authorization process:
    
            ./nokia-weight-sync.py -k CLIENT_ID -s CLIENT_SECRET setup smashrun
            
5. Verify that the relevant sections for the services are added to ```config.ini```.
        
6. Synchronize (new) measurements:

        ./nokia-weight-sync.py sync garmin
        ./nokia-weight-sync.py sync smashrun
        
**Important** Nokia Health API, Smashrun API, and Garmin Connect credentials are stored in ```config.ini```. If this file is compromised your Garmin Connect account, personal health data from Nokia Health, and activity data from Smashrun are at risk.
        
## Advanced

See ```./nokia-weight-sync.py --help``` for more information.

## Notice

nokia-weight-sync includes components the following open-source projects:

* ```fit.py``` from [ikasamah/withings-garmin](https://github.com/ikasamah/withings-garmin), MIT License (c) 2013 Masayuki Hamasaki, adapted for Python 3.
* ```garmin.py``` from [jaroslawhartman/withings-garmin-v2](https://github.com/jaroslawhartman/withings-garmin-v2), MIT License (c) 2013 Masayuki Hamasaki, adapted for Python 3.
* ```nokia.py``` from [python-nokia](https://github.com/orcasgit/python-nokia), MIT License (c) 2012 Maxime Bouroumeau-Fuseau, 2017 ORCAS, unmodified.
* ```sessioncache.py``` from [cpfair/tapiriik](https://github.com/cpfair/tapiriik/blob/187d1b97ce73cc35b5e2194eb4631ceff20499e3/tapiriik/services/sessioncache.py), Apache License 2.0, unmodified.
* ```smashrun.py``` from [campbellr/smashrun-client](https://github.com/campbellr/smashrun-client), Apache License 2.0, several fixes.

## Support

Please [open an issue](https://github.com/magnific0/nokia-weight-sync/issues/new) for support.

## Contributing

Please contribute using [Github Flow](https://guides.github.com/introduction/flow/). Create a branch, add commits, and [open a pull request](https://github.com/magnific0/nokia-weight-sync/compare/).
