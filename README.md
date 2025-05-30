- 👋 Hi, I’m @prottoy-ahmed69
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
const axios = require("axios");

module.exports = {
    config: {
        name: "nsfw",
        aliases: [],
        version: "1.4",
        author: "TawsiN",
        countDown: 3,
        role: 0,
        longDescription: "Get a random NSFW anime waifu image.",
        category: "nsfw",
        guide: {
            en: "Usage:\n\n{pn} - Get a random NSFW waifu image."
        }
    },

    onStart: async function ({ message }) {
        try {
            const { data } = await axios.get("https://api.waifu.pics/nsfw/waifu");

            if (!data.url) throw new Error("Failed to fetch waifu image.");

            await message.reply({
                body: "Here's your NSFW waifu! 🔥",
                attachment: await global.utils.getStreamFromURL(data.url)
            });

        } catch (error) {
            message.reply(`⚠️ Error: ${error.message}`);
        }
    }
};
<!---
prottoy-ahmed69/prottoy-ahmed69 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
