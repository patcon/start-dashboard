# StART Dashboard: Developer Docs

Note: To find any pre-created credentials for this project, please see the [StART Digital Tools and Services](https://docs.google.com/document/d/1UTIEjy1KRCjGA6yQ7SQBBm5yi-QKoFJyaIfMVR7XzhI/edit?usp=sharing) doc (you'll need to get access).

## Credentials

You'll need the following credentials in your `.env` file in the project's root directory.

```
REACT_APP_GOOGLE_MAPS_API_KEY=
REACT_APP_AUTH0_DOMAIN=
REACT_APP_AUTH0_CLIENT_ID=
REACT_APP_AIRTABLE_TOKEN=
REACT_APP_AIRTABLE_BASE=
```

## Auth0 Account

The Auth0 credentials need to be for the StART Digital application on Auth0, which uses custom Rules to fetch user data from Airtable. You can see the code for the custom rules at `docs/auth0-rules.md` if you want to recreate them on another account.

Ask one of the current admins to add you as an admin to the StART Digital dashboard on Auth0.

If you're recreating the setup on a new account:

1. Create an auth0 account
2. Visit your applications listing page: https://manage.auth0.com/#/applications/
3. Click the app name, "Default App" or create a new app for this purpose.
4. In the "Settings" tab:
    - Note the Domain and enter it as `REACT_APP_AUTH0_DOMAIN` in your `.env` config.
    - Note the Client ID and enter it as `REACT_APP_AUTH0_CLIENT_ID` in your `.env` config.
5. Under "Allowed Callback URLs", enter `http://localhost:3000`
6. Go to the [Rules page](https://manage.auth0.com/dashboard/us/start-dashboard/rules) and create the two rules documented in `docs/auth0-rules.md`.

## Google Maps API Key

Use the API key documented in [StART Digital Tools and Services](https://docs.google.com/document/d/1UTIEjy1KRCjGA6yQ7SQBBm5yi-QKoFJyaIfMVR7XzhI/edit?usp=sharing) or create your own by following the instructions [here](https://developers.google.com/maps/documentation/javascript/get-api-key).

Your API key will need to have the following APIs enabled:
- Maps JavaScript API
- Geocoding API

## Airtable API Key

This credential is used to modify data in Airtable from the dashboard.

Warning: These keys work at the **user level**, and so your API key will allow
any modifications that your Airtable user account allows.

Given the above, the API key / account should ideally have:
- a permission scope on your database no greater than required: `editor`, rather than `creator` or `owner`.
- access to only databases that are required by the dashboard, ie. `StART V3` database.

You may wish to create a new user to meet the above recommendations.

All configuration mentioned will be added to your `.env` file in the project's root directory.

1. Log into the Airtable account you'd like to use for API access.
2. Visit the database, and note the base ID in the URL (the part of path beginning with `appXXXXXXX`).
    - Enter this as `START_AIRTABLE_BASE` in your `.env` config.
3. Visit your account page: https://airtable.com/account
4. Generate an API key if it doesn't already exist.
5. Enter this key as `START_AIRTABLE_TOKEN` in your `.env` config.
