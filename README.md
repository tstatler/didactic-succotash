# Zoom Webhook Sample

A Node.js / Express server that receives [Zoom Platform Webhooks](https://developers.zoom.us/docs/api/rest/webhook-reference/#enable-webhooks) and [Zoom Video SDK Webhooks](https://developers.zoom.us/docs/api/rest/webhook-reference/#enable-webhooks).

Based on [zoom/webhook-sample](https://github.com/zoom/webhook-sample).

## Installation

In terminal, run the following command to clone the repo:

```
$ git clone https://github.com/tstatler/didactic-succotash.git
```

## Setup

1. In terminal, cd into the cloned repo:

   ```
   $ cd didactic-succotash
   ```

2. Then install the dependencies:

   ```
   $ npm install
   ```

3. Create an environment file to store your Webhook Secret Token:

   ```
   $ cp .env.example .env
   ```

4. Add your [Zoom Webhook Secret Token](https://developers.zoom.us/docs/api/rest/webhook-reference/#verify-webhook-events) to the `.env` file:

   ```
   ZOOM_WEBHOOK_SECRET_TOKEN=your_token_here
   ```

5. Save and close `.env`.

6. Start the server:

   ```
   $ npm run start
   ```

7. Expose the local server to the internet using [Ngrok](https://ngrok.com) (free):

   ```
   $ ngrok http 4000
   ```

8. Copy the ngrok https URL and paste it in the Event notification endpoint URL on your Zoom App's Features section. Remember to include the `/webhook` path.

   Example: `https://abc123.ngrok.io/webhook`

9. Click **Validate**, then choose the events you'd like to subscribe to, and click **Save**.

## Usage

The server exposes two endpoints:

- `GET /` – Health check endpoint.
- `POST /webhook` – Receives Zoom webhook events. Verifies the request signature and handles `endpoint.url_validation` for Zoom endpoint validation.

## License

Use of this sample app is subject to our [Terms of Use](https://explore.zoom.us/en/legal/zoom-api-license-and-tou/).