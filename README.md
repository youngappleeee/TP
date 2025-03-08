-- Teletransporte con iniciales y GUI
local Gui = Instance.new("ScreenGui", game.Players.LocalPlayer:WaitForChild("PlayerGui"))
local Frame = Instance.new("Frame", Gui)
Frame.Size = UDim2.new(0, 300, 0, 200)
Frame.Position = UDim2.new(0.5, -150, 0.5, -100)
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.Visible = false

local TextBox = Instance.new("TextBox", Frame)
TextBox.Size = UDim2.new(0, 200, 0, 50)
TextBox.Position = UDim2.new(0.5, -100, 0.2, 0)
TextBox.PlaceholderText = "Ingresa las 3 iniciales"

local Button = Instance.new("TextButton", Frame)
Button.Size = UDim2.new(0, 200, 0, 50)
Button.Position = UDim2.new(0.5, -100, 0.6, 0)
Button.Text = "TP"
Button.BackgroundColor3 = Color3.fromRGB(0, 255, 0)

Button.MouseButton1Click:Connect(function()
    local iniciales = TextBox.Text
    if #iniciales == 3 then
        for _, player in pairs(game.Players:GetPlayers()) do
            if player.Name:sub(1, 3):lower() == iniciales:lower() then
                game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(player.Character.HumanoidRootPart.CFrame)
                break
            end
        end
    end
end)

game:GetService("UserInputService").InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.B then
        Frame.Visible = not Frame.Visible
    end
end)
