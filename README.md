![Pinterest Scraper Featured Image](https://raw.githubusercontent.com/omkarcloud/pinterest-scraper/master/pinterest-scraper-featured-image.png)

# Pinterest Scraper API

Search Pinterest profiles, get full profile details with bios and social links, pull pin feeds with multi-resolution images, and list boards — all via a simple REST API. 5,000 free requests/month.

## Key Features

- Search Pinterest profiles by keyword or handle
- Get 20+ data points per profile (followers, bio, avatars, Instagram link, website)
- Fetch a creator's pin feed with 4 image resolutions per pin
- List profile boards with engagement metrics
- **5,000 requests/month on free tier**
- Example Response:
```json
{
    "user_id": "887842651448232609",
    "username": "homedecor",
    "display_name": "Home Decor",
    "followers": 16234,
    "total_pins": 10712,
    "total_boards": 239,
    "has_custom_avatar": true,
    "avatars": {
        "small": "https://i.pinimg.com/30x30_RS/20/ee/75/20ee75eb55a815f82f1fa6617233d83d.jpg",
        "medium": "https://i.pinimg.com/75x75_RS/20/ee/75/20ee75eb55a815f82f1fa6617233d83d.jpg",
        "large": "https://i.pinimg.com/140x140_RS/20/ee/75/20ee75eb55a815f82f1fa6617233d83d.jpg"
    },
    "is_verified_merchant": false,
    "is_domain_verified": false,
    "last_active": "1week"
}
```

## Get API Key

Create an account at [omkar.cloud](https://www.omkar.cloud/auth/sign-up?redirect=/api-key) to get your API key.

It takes just 2 minutes to sign up. You get 5,000 free requests every month for detailed Pinterest data — more than enough for most users to get their job done without paying a dime.

This is a well built product, and your search for the best Pinterest Scraper API ends right here.


## Quick Start

```bash
curl -X GET "https://pinterest-scraper.omkar.cloud/pinterest/search?search_term=home%20decor" \
  -H "API-Key: YOUR_API_KEY"
```

```json
{
  "total_results": 50,
  "profiles": [
    {
      "user_id": "887842651448232609",
      "username": "homedecor",
      "display_name": "Home Decor",
      "followers": 16234,
      "total_pins": 10712,
      "total_boards": 239,
      "has_custom_avatar": true,
      "is_verified_merchant": false,
      "is_domain_verified": false,
      "last_active": "1week"
    }
  ]
}
```

## Quick Start (Python)

```bash
pip install requests
```

```python
import requests

response = requests.get(
    "https://pinterest-scraper.omkar.cloud/pinterest/search",
    params={"search_term": "home decor"},
    headers={"API-Key": "YOUR_API_KEY"}
)

print(response.json())
```


## API Reference

### Profile Discovery

```
GET https://pinterest-scraper.omkar.cloud/pinterest/search
```

#### Parameters

| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `search_term` | Yes | — | Keyword or handle to search Pinterest profiles. |

#### Example

```python
import requests

response = requests.get(
    "https://pinterest-scraper.omkar.cloud/pinterest/search",
    params={"search_term": "home decor"},
    headers={"API-Key": "YOUR_API_KEY"}
)

print(response.json())
```

#### Response

<details>
<summary>Sample Response (click to expand)</summary>

```json
{
  "total_results": 50,
  "profiles": [
    {
      "user_id": "887842651448232609",
      "username": "homedecor",
      "display_name": "Home Decor",
      "followers": 16234,
      "total_pins": 10712,
      "total_boards": 239,
      "has_custom_avatar": true,
      "avatars": {
        "small": "https://i.pinimg.com/30x30_RS/20/ee/75/20ee75eb55a815f82f1fa6617233d83d.jpg",
        "medium": "https://i.pinimg.com/75x75_RS/20/ee/75/20ee75eb55a815f82f1fa6617233d83d.jpg",
        "large": "https://i.pinimg.com/140x140_RS/20/ee/75/20ee75eb55a815f82f1fa6617233d83d.jpg",
        "extra_large": "https://i.pinimg.com/140x140_RS/20/ee/75/20ee75eb55a815f82f1fa6617233d83d.jpg"
      },
      "is_verified_merchant": false,
      "is_domain_verified": false,
      "last_active": "1week",
      "preview_pin_thumbnails": [
        "https://i.pinimg.com/75x75/1f/19/6f/1f196fd05b0d8eb0f4aebc989ebba078.jpg",
        "https://i.pinimg.com/75x75/32/3b/2d/323b2d077c476ea66b43e20516f4fad3.jpg",
        "https://i.pinimg.com/75x75/30/81/00/308100f216f65c0e10c1df654ecc841f.jpg"
      ],
      "recent_pins_gallery": [
        {
          "url": "https://i.pinimg.com/222x/1f/19/6f/1f196fd05b0d8eb0f4aebc989ebba078.jpg",
          "width": 222,
          "height": 402,
          "primary_color": "#888077"
        }
      ]
    }
  ]
}
```

</details>

---

### Profile Details

```
GET https://pinterest-scraper.omkar.cloud/pinterest/profile
```

#### Parameters

| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `username` | Yes | — | Pinterest username to fetch details for. |

#### Example

```python
import requests

response = requests.get(
    "https://pinterest-scraper.omkar.cloud/pinterest/profile",
    params={"username": "ohjoy"},
    headers={"API-Key": "YOUR_API_KEY"}
)

print(response.json())
```

#### Response

<details>
<summary>Sample Response (click to expand)</summary>

```json
{
  "user_id": "21181198155907073",
  "username": "ohjoy",
  "display_name": "Joy Cho / Oh Joy!",
  "first_name": "Joy Cho / Oh Joy!",
  "bio": "👩🏻 Founder and Creative Director of Oh Joy!  • Entrepreneur💡• Designer 🎨 • Author 📚• Small Biz Mentor 📊 • Mama 👭🏻 • Thai American 🇹🇭 • Tennis Player 🎾 @JoyOnTheCourt • LA 📍",
  "avatars": {
    "medium": "https://i.pinimg.com/75x75_RS/9a/44/f6/9a44f6b6bffba5e3bc1de97f92d346c1.jpg",
    "extra_large": "https://i.pinimg.com/280x280_RS/9a/44/f6/9a44f6b6bffba5e3bc1de97f92d346c1.jpg"
  },
  "followers": 15103638,
  "following": 407,
  "total_pins": 34402,
  "total_boards": 74,
  "interests_followed": 5,
  "website": "http://linktr.ee/ohjoy",
  "is_private": false,
  "is_verified_merchant": false,
  "is_domain_verified": false,
  "is_website_verified": false,
  "is_partner": true,
  "instagram": {
    "url": "https://www.instagram.com/ohjoy",
    "username": "ohjoy"
  },
  "impressum_url": null,
  "account_created_at": "Thu, 29 Apr 2010 21:28:02 +0000",
  "last_pin_saved_at": "Wed, 04 Feb 2026 05:35:42 +0000",
  "profile_tabs": [
    {
      "tab_id": "16890156189292",
      "name": "Created",
      "kind": 1,
      "is_default": false
    },
    {
      "tab_id": "16890089225413",
      "name": "Saved",
      "kind": 0,
      "is_default": true
    }
  ],
  "cover": {
    "images": {
      "originals": {
        "url": "https://i.pinimg.com/originals/58/d4/f7/58d4f71b38696d35479edc517ecae08f.jpg",
        "width": 2000,
        "height": 1125
      }
    }
  },
  "is_indexed": true
}
```

</details>

---

### Profile Pins Feed

```
GET https://pinterest-scraper.omkar.cloud/pinterest/pins
```

#### Parameters

| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `username` | Yes | — | Pinterest username whose pins to return. |

#### Example

```python
import requests

response = requests.get(
    "https://pinterest-scraper.omkar.cloud/pinterest/pins",
    params={"username": "ohjoy"},
    headers={"API-Key": "YOUR_API_KEY"}
)

print(response.json())
```

#### Response Fields

Returns per pin: title, description, multi-resolution images (170x, 236x, 474x, 736x), board info, author info, reactions, saves, source URL, product data, and permalink.

<details>
<summary>Sample Response (click to expand)</summary>

```json
{
  "total_results": 24,
  "pins": [
    {
      "pin_id": "21181060743951564",
      "title": null,
      "grid_title": "Instax mini Rolodex | Photo Display Stand | Wedding Guestbook | Personalized Gift",
      "description": "Instax Mini Polaroid Rolodex - Marble & Pastel Editions Keep your memories beautifully displayed with this 3D printed Instax Mini Rolodex...",
      "alt_text": null,
      "auto_generated_alt_text": null,
      "source_url": "https://www.etsy.com/listing/4357445470/instax-mini-rolodex-photo-display-stand",
      "source_domain": "etsy.com",
      "created_at": "Wed, 04 Feb 2026 05:35:42 +0000",
      "dominant_color": "#bcada2",
      "is_video": null,
      "images": {
        "170x": {
          "url": "https://i.pinimg.com/236x/6e/65/9b/6e659b8f77c6d2a30dec96008812fb14.jpg",
          "width": 236,
          "height": 354
        },
        "236x": {
          "url": "https://i.pinimg.com/236x/6e/65/9b/6e659b8f77c6d2a30dec96008812fb14.jpg",
          "width": 236,
          "height": 354
        },
        "474x": {
          "url": "https://i.pinimg.com/474x/6e/65/9b/6e659b8f77c6d2a30dec96008812fb14.jpg",
          "width": 474,
          "height": 711
        },
        "736x": {
          "url": "https://i.pinimg.com/736x/6e/65/9b/6e659b8f77c6d2a30dec96008812fb14.jpg",
          "width": 736,
          "height": 1104
        }
      },
      "videos": null,
      "board": {
        "board_id": "21181129436430338",
        "name": "For the Home",
        "url": "/ohjoy/for-the-home/",
        "privacy": "public",
        "thumbnail_url": "https://i.pinimg.com/upload/21181129436430338_board_thumbnail_2026-01-28-18-53-21_18765_60.jpg"
      },
      "author": {
        "user_id": "21181198155907073",
        "username": "ohjoy",
        "display_name": "Joy Cho / Oh Joy!",
        "avatar_url": "https://i.pinimg.com/30x30_RS/9a/44/f6/9a44f6b6bffba5e3bc1de97f92d346c1.jpg",
        "is_verified_merchant": false
      },
      "reactions": {
        "1": 129
      },
      "saves": null,
      "comment_count": null,
      "permalink": "/pin/21181060743951564/",
      "embed": null,
      "product_data": null,
      "is_product": false,
      "shopping_flags": [5]
    }
  ]
}
```

</details>

---

### Profile Boards

```
GET https://pinterest-scraper.omkar.cloud/pinterest/boards
```

#### Parameters

| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `username` | Yes | — | Pinterest username whose boards to return. |

#### Example

```python
import requests

response = requests.get(
    "https://pinterest-scraper.omkar.cloud/pinterest/boards",
    params={"username": "ohjoy"},
    headers={"API-Key": "YOUR_API_KEY"}
)

print(response.json())
```

#### Response

<details>
<summary>Sample Response (click to expand)</summary>

```json
{
  "total_results": 2,
  "items": [
    {
      "item_id": "450430400252983295",
      "title": "ZURU Snackles = squishy plush + surprise snack toy! 🍔🧸 Cute, collectible & cuddly—your kids will want them ALL!",
      "description": "ZURU Snackles = squishy plush + surprise snack toy! 🍔🧸 Cute, collectible & cuddly—your kids will want them ALL!",
      "dominant_color": "#fe7ca9",
      "saves": 0,
      "comment_count": 0,
      "created_at": "Fri, 04 Jul 2025 01:40:21 +0000",
      "is_video": false,
      "rich_metadata": null,
      "creator": {
        "user_id": "93027685961303976",
        "username": "queenval1967",
        "display_name": "Rising Star Events ~ Online Vendor Events",
        "avatar_urls": {
          "small": "https://i.pinimg.com/30x30_RS/69/53/80/6953809268843ea70de1cf6fe5bc7e7a.jpg",
          "medium": "https://i.pinimg.com/75x75_RS/69/53/80/6953809268843ea70de1cf6fe5bc7e7a.jpg",
          "large": "https://i.pinimg.com/140x140_RS/69/53/80/6953809268843ea70de1cf6fe5bc7e7a.jpg"
        },
        "is_verified_merchant": false
      }
    }
  ]
}
```

</details>

## Error Handling

```python
response = requests.get(
    "https://pinterest-scraper.omkar.cloud/pinterest/search",
    params={"search_term": "home decor"},
    headers={"API-Key": "YOUR_API_KEY"}
)

if response.status_code == 200:
    data = response.json()
elif response.status_code == 401:
    # Invalid API key
    pass
elif response.status_code == 429:
    # Rate limit exceeded
    pass
```

## FAQs

### What data does the API return?

**Profile Discovery** returns per profile:
- User ID, username, display name
- Follower count, total pins, total boards
- Avatar URLs (4 sizes), custom avatar flag
- Verified merchant and domain status
- Last active time, preview pin thumbnails, recent pins gallery

**Profile Details** returns per profile:
- Full bio, first name, display name
- Follower and following counts
- Total pins, boards, and interests followed
- Website URL, Instagram link
- Account creation date, last pin saved date
- Profile cover images, profile tabs
- Privacy, partner, verification, and indexing status

**Profile Pins Feed** returns per pin:
- Pin ID, title, grid title, description
- Alt text, auto-generated alt text
- Source URL, source domain
- Multi-resolution images (170x, 236x, 474x, 736x)
- Board info (name, URL, privacy, thumbnail)
- Author info (username, display name, avatar)
- Reactions, saves, comments, permalink
- Product and shopping data

**Profile Boards** returns per board item:
- Item ID, title, description
- Dominant color, saves, comment count
- Creation date, video flag
- Creator info (username, display name, avatar URLs)

All in structured JSON. Ready to use in your app.

### How accurate is the data?

Data is pulled from Pinterest in real time. Every API call fetches live data — not cached or stale results. Follower counts, pin details, boards, and bios reflect what's on Pinterest right now.

### Can I search by keyword or username?

Both. The Profile Discovery endpoint takes any keyword — `home decor`, `travel`, `fashion` — and returns matching profiles.

For specific users, pass their username directly to Profile Details, Pins, or Boards endpoints.

### Does the API return Instagram and website links?

Yes. The Profile Details endpoint returns linked Instagram link and the profile's website URL when available.

## Rate Limits

| Plan | Price | Requests/Month |
|------|-------|----------------|
| Free | $0 | 5,000 |
| Starter | $25 | 100,000 |
| Grow | $75 | 1,000,000 |
| Scale | $150 | 10,000,000 |

## Questions? We have answers.

Reach out anytime. We will solve your query within 1 working day.

[![Contact Us on WhatsApp about Pinterest Scraper](https://raw.githubusercontent.com/omkarcloud/assets/master/images/whatsapp-us.png)](https://api.whatsapp.com/send?phone=918178804274&text=I%20have%20a%20question%20about%20the%20Pinterest%20Scraper%20API.)

[![Contact Us on Email about Pinterest Scraper](https://raw.githubusercontent.com/omkarcloud/assets/master/images/ask-on-email.png)](mailto:happy.to.help@omkar.cloud?subject=Pinterest%20Scraper%20API%20Question)
