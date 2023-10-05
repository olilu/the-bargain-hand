# The Bargain Hand
The Bargain Hand is a web application for scraping game prices in the Nintendo eShop and the PlayStation Store for bargains. You can manage your own wishlist in a web UI and get email alerts once they are on sale.
## Getting Started
In this repository you will find all the ressources necessary to spin up your own Bargain Hand application with Docker. Follow the few steps below and start bargain hunting in the Nintendo eShop and the PlayStation Store.

1. Clone this repository or copy the docker-compose.yml to a location on a system with docker installed.
2. Navigate to the location of the docker-compose.yml
3. Specify and load the following environment variables in your session
```bash
POSTGRES_USER=dbadmin
POSTGRES_PASSWORD= # define password here
POSTGRES_PORT=5432
POSTGRES_DB=bargaindb
POSTGRES_SERVER=pgdb
SMTP_SERVER= # smtp Server to send bargain emails from
SMTP_PORT= # smtp port
SMTP_SENDER_EMAIL= # email address that should send the bargain alerts
SMTP_SENDER_PASSWORD= # password for your sender email address

###### Optional #######
PGADMIN_DEFAULT_EMAIL=pgadmin@admin.com
PGADMIN_DEFAULT_PASSWORD= # define password here
```
4. create the docker composition
```bash
docker compose up -d
```
5. Open a web browser and navigate to the docker host with the port specified for the frontend in the docker-compose.yml. The default is set to port 3000.
```bash
# Example for local installation with default port 3000:
http://localhost:3000
```
## Usage Advice
* The Bargain Hand supports different locations, though not all of them are tested. Following country and language settings are tested:
    - CH_de
    - CH_fr
    - GB_en
    - DE_de
* For all countries not using the European Nintendo eShop version, the UI will not display any pictures for Nintendo games. This is due to Nintendo basically running 3 different shops, which makes the "european" image scraper fail for the other shop regions. 
    - Big shout out at this point to @fedecalendino the creator of [Nintendeals](https://pypi.org/project/nintendeals/) for creating a price scraper for ALL Nintendo eShop regions! The Bargain Hand heavily relies on this module.
* Don't create wishlists with different country settings on the same Bargain Hand instance. If you do, the price alerting should still work, but the links to the games in the UI and the emails might point to the wrong store region.
